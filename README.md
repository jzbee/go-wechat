# go-wechat

golang 微信公众号 sdk

源码出自 地址:https://github.com/MwlLj/go-wechat

本项目只是在源码基础上做修改以及新功能

# install
` go get https://github.com/jzbee/go-wechat `

# sample example

```
package main
import (
	"fmt"
	"github.com/jzbee/go-wechat"
	"github.com/jzbee/go-wechat/common"
)

var _ = fmt.Println

func main() {
	info := common.CUserInfo{
		AppId:     "your appid",
		AppSecret: "your appsecret",
		Port:      80,
		Url:       "/xxx",
		Token:     "your token",
	}
	wc := wechat.New(&info)
	wc.RegisterMsgFunc(func(reply common.IReply, msg *common.CMessage,communicate common.CDataCommunicate, userData interface{}) error {
		reply.SendMessage(msg)
		return nil
	}, nil)
	wc.Loop()
}
```
