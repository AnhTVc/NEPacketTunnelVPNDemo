Apple released a new version of `Network Extension` since iOS9, which allows us to implement our own VPN protocol. This repo provides a simple demo using `Network Extension` with Swift 3.

Server side demo is [here](https://github.com/lxdcn/simple-vpn-demo).

This demo and server side demo are extremely simplified and only for demonstration purposes, a lot of stuff are hard coded. Further design and elaboration are required if you want apply this demo to your app.

## build app in ios

1. First you need an iPhone. Network Extension App cannot run in iOS Simulators, you need a real iPhone to debug.

2. Login Apple [developer portal](https://developer.apple.com/account/ios/certificate), register 2 new App IDs, one for App target and another for NetworkExtension tunnel target. And make sure `App Groups` and `Network Extensions` are checked in `App Services` section.

3. Register an `App Group` in developer portal as well

4. Then, again in `App IDs` section of developer portal, edit the 2 App IDs you created at 3rd step, configure `App Groups` to the app group you created at 4th step.

5. Also in developer portal, generate 2 iOS App Development provision profiles for the 2 App IDs created before, make sure `Network Extension` entitlement is selected on 'Do you need additional entitlements?' page. Then download them and save them to disk.

6. Open this xcodeproj with XCode, select `NEPacketTunnelVPNDemo` target, in `General > Identity` section, change `Bundle Identifier` to App ID you created. Then import profiles you generated in `General > Signing (Debug)` section and `General > Signing (Release)` section.

7. Do the same thing for extention `NEPacketTunnelVPNDemoTunnel` target.

## build server vpn in server and run test

1. clone project simple vpn [here](https://github.com/lxdcn/simple-vpn-demo) in server linux (require gcc - install gcc in ubuntu "apt-get install gcc")
2. cd folder simple-vpn-demo run ()
    $make
    $./vpn
3. server open port: 54345 for UDP. 
4. After build & run `NEPacketTunnelVPNDemo` on your iPhone, change IP server in file [ViewController.swift](https://github.com/AnhTVc/NEPacketTunnelVPNDemo/blob/master/NEPacketTunnelVPNDemo/ViewController.swift).
    let serverAddress = "<ip-server>"
5. The `Connect` at the center of iPhone screen is a **BUTTON**
