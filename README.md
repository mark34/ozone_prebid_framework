# ozone_prebid_framework


## clone the repo & use the frameworks without need to build. Just drag the xxxxx.xcframework folder into your ios project. Android to follow.


How to implement Ozone Prebid iOS framework for header bidding


XCode: 


Import the google ad & usercentrics Podfiles:
=============================================

- It turns out the cocopapods doesn't know how to work with Xcode 14 project version properly.
- To solve the issue, open Xcode project on the right side utility panel and change the project version to Xcode 13.0 - compatible and you are good to go.
- create a Podfile:
- cd (your dir) then create `Podfile` containing:

platform :ios, '11.0'
use_frameworks!

target '[your project folder]' do 
    pod 'Google-Mobile-Ads-SDK'
    pod 'UsercentricsUI', '2.7.14'
end

- cd (your dir) then execute:
- pod install
- reopen by opening the xcworkspace file (close xcode & rightclick the new xcworkspace file that's just been generated)


Import the Ozone Prebid framework:
==================================
- Drag the XCPrebidMobile.xcframework file in to the project (into 'Frameworks' or wherever you prefer in your app), select copy (yes), create groups, add to targets: (All)
- menu: Build Phases -> link binary with binaries -> add XCPrebidMobile.xcframework (required)
- menu: General -> Frameworks, Libraries & Embedded content -> XCPrebidMobile.xcframework -> 'Embed & Sign' (else you won't be able to build for a real device)
- add helper file to your project: UserCentricsHelper.swift


View Controllers & UI:
======================

- place a 'view' component on the page to contain the ad
- at the top of your swift files: 

import UIKit
import PrebidMobile
import GoogleMobileAds
import ObjectiveC.runtime
import Usercentrics
import UsercentricsUI
import CoreLocation

- see the demo app for exactly how to request bids & render ads into your view component.




Known issues
============

There may be a memory or other issue with webkit which may present itself if you render video ads on certain devices/ios versions:
https://github.com/ionic-team/ionic-framework/issues/25760




