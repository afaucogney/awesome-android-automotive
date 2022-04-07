# Awesome Android Automotive

Objectifs :
- Update sur les architectures auto
- Quoi de neuf sur AutoSar depuis 10 ans
- Android Auto
- Android Automotive (cote OEM)
- Android Automotive (cote App maker)

## Resources

- [How to build a Android Automotive App](https://youtu.be/AHHERLwjUGo) during I/O 2019
  - Android Auto / Automotive app are quite same in terme of implementation
  - Dedicated module must be implemented for both AA and AAOS
  - Business logic should be shared in a commun module with the App
  - There is no launchqble activity in AAOS App
  - Distraction is almost handle by OS
  - Permission if reauired, should be ask asap (sign in for exemple)
  - Sign in may be done with login, BT, other


- [An introduction to Android Automotive OS](https://youtu.be/KVM5njlZ4sM) by Chris Simmonds qt NDC TechnTowns
  - Android Auto in 2014
  - AAOS in 2017
  - Android in IVI already in market (Honda JB 4.2, Hundai GB 2.3, Renault 4.1)  
  - AAOS part of AOSP
  - AAOS is not production ready, it need to be adpated by OEM
  - GAS (Google Automotive Service) is not free, and include Store, Assistant and Map)
    - Per unit license
    - Must pass test CTS, VTS, ATS
    - Must install google apps
 
 ```mermaid
 graph TD
    A(Car app) --> B(Car manager)
    B --> |ICar AIDL interfaces| C(Car service)
    C --> |IVehicle HIDL interfaces| D(Vehicle HAL)
    D --> |Vechile bus| E(Vehicle ECUs)
 ```
 
  - Vehicle property is car signal available in AAOS
  - It does exist more than 150 property of group VEchilePropertyCroup:System
  - Vendors can add preperty marked VEchilePropertyCroup:Vendor
    - must be added in native as well as java, with it type, an its area and with a uniq ID
  - Vehicle property may have different changeMode static, on_change, continuous (subscription with sampling rate)
  - May list vechile property with dumpsys car_service (-h with list of option)
  - Car maner is the APi for the car service (android.car.jar)
  - Car manager provides 23 interfaces
    - App needs to get permission to get car services
    - Only a few are available
      - CAR_INFO
      - READ_CAR_DISPLAY_UNITS
      - CONTROL_CAR_DISPLAY_UNITS
      - CAR_ENERGY_PORTS
      - CAR_EXTERIOR_ENVIRONMENT
      - CAR_POWERTRAIN
      - CAR_SPEED
      - CAR_ENERGY
    - Others are for OEM only (marked as signature|privileged), ship with OS
      - to access vendor property, app need PERMISSION_VENDOR_EXTENSION (level priviledged) 
  - AAOS is not SCOS, as it may crash
  - Car app is really controlled and restricted (distraction free)
  - Should have GAS to publsih on Store
  - Only those type are available
    - media
    - messaging using voice
    - nav, parking, charging
  - Only 30 apps for automotive and 400 general apps  (early 2021)
  - RearViewCamera is a self contained app (in c++) with EVS (exterior view system)
    - EVS and Android can not show info in same time
  - Audio is managed by audio flinger, that handle wave in many bus (group of speaker)
    - based on audio context  
    - warning is not handle by AAOS 

  - link : [2net](https://2net.co.uk/)
  - https://2net.co.uk/videos


 - [Android Bootcamp](https://source.android.com/devices/automotive/start/presentations) slides


 - [Linux Plumber Micro Conf about Android](https://lpc.events/event/16/page/193-proposed-microconferences#android)


 - [Android Automotive OS Discussion Group](https://groups.google.com/a/android.com/g/automotive-developers?pli=1)
