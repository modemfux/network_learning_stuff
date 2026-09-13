# BASE CONFIGURATION

**Leaf-1:**

```arista
hostname Leaf-1
!
interface Ethernet5
   no switchport
   ip address 10.1.5.1/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Ethernet6
   no switchport
   ip address 10.1.6.1/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Loopback0
   ip address 10.0.0.1/32
!
interface Loopback1
   ip address 10.0.0.101/32
!
ip routing
!
router bgp 65000
   router-id 10.0.0.1
   no bgp default ipv4-unicast
   neighbor RR peer group
   neighbor RR remote-as 65000
   neighbor RR update-source Loopback0
   neighbor RR send-community standard extended
   neighbor 10.0.0.5 peer group RR
   neighbor 10.0.0.6 peer group RR
   !
   address-family evpn
      neighbor RR activate
!
router ospf 1
   router-id 10.0.0.1
   network 10.0.0.0/8 area 0.0.0.0
   max-lsa 12000
!
```

**Leaf-2:**

```arista
hostname Leaf-2
!
interface Ethernet5
   no switchport
   ip address 10.2.5.2/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Ethernet6
   no switchport
   ip address 10.2.6.2/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Loopback0
   ip address 10.0.0.2/32
!
interface Loopback1
   ip address 10.0.0.102/32
!
ip routing
!
router bgp 65000
   router-id 10.0.0.2
   no bgp default ipv4-unicast
   neighbor RR peer group
   neighbor RR remote-as 65000
   neighbor RR update-source Loopback0
   neighbor RR send-community standard extended
   neighbor 10.0.0.5 peer group RR
   neighbor 10.0.0.6 peer group RR
   !
   address-family evpn
      neighbor RR activate
!
router ospf 1
   router-id 10.0.0.2
   network 10.0.0.0/8 area 0.0.0.0
   max-lsa 12000
!
```

**Leaf-3:**

```arista
hostname Leaf-3
!
interface Ethernet5
   no switchport
   ip address 10.3.5.3/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Ethernet6
   no switchport
   ip address 10.3.6.3/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Loopback0
   ip address 10.0.0.3/32
!
interface Loopback1
   ip address 10.0.0.103/32
!
ip routing
!
router bgp 65000
   router-id 10.0.0.3
   no bgp default ipv4-unicast
   neighbor RR peer group
   neighbor RR remote-as 65000
   neighbor RR update-source Loopback0
   neighbor RR send-community standard extended
   neighbor 10.0.0.5 peer group RR
   neighbor 10.0.0.6 peer group RR
   !
   address-family evpn
      neighbor RR activate
!
router ospf 1
   router-id 10.0.0.3
   network 10.0.0.0/8 area 0.0.0.0
   max-lsa 12000
!
```

**Leaf-4:**

```arista
hostname Leaf-4
!
interface Ethernet5
   no switchport
   ip address 10.4.5.4/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Ethernet6
   no switchport
   ip address 10.4.6.4/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Loopback0
   ip address 10.0.0.4/32
!
interface Loopback1
   ip address 10.0.0.104/32
!
ip routing
!
router bgp 65000
   router-id 10.0.0.4
   no bgp default ipv4-unicast
   neighbor RR peer group
   neighbor RR remote-as 65000
   neighbor RR update-source Loopback0
   neighbor RR send-community standard extended
   neighbor 10.0.0.5 peer group RR
   neighbor 10.0.0.6 peer group RR
   !
   address-family evpn
      neighbor RR activate
!
router ospf 1
   router-id 10.0.0.4
   network 10.0.0.0/8 area 0.0.0.0
   max-lsa 12000
!
```

**Spine-5:**

```arista
hostname Spine-5
!
interface Ethernet1
   no switchport
   ip address 10.1.5.5/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Ethernet2
   no switchport
   ip address 10.2.5.5/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Ethernet3
   no switchport
   ip address 10.3.5.5/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Ethernet4
   no switchport
   ip address 10.4.5.5/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Loopback0
   ip address 10.0.0.5/32
!
interface Loopback1
   ip address 10.0.0.105/32
!
ip routing
!
router bgp 65000
   router-id 10.0.0.5
   no bgp default ipv4-unicast
   neighbor RRC peer group
   neighbor RRC remote-as 65000
   neighbor RRC update-source Loopback0
   neighbor RRC route-reflector-client
   neighbor RRC send-community standard extended
   neighbor 10.0.0.1 peer group RRC
   neighbor 10.0.0.2 peer group RRC
   neighbor 10.0.0.3 peer group RRC
   neighbor 10.0.0.4 peer group RRC
   !
   address-family evpn
      neighbor RRC activate
!
router ospf 1
   router-id 10.0.0.5
   network 10.0.0.0/8 area 0.0.0.0
   max-lsa 12000
!
```

**Spine-6:**

```arista
hostname Spine-6
!
interface Ethernet1
   no switchport
   ip address 10.1.6.6/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Ethernet2
   no switchport
   ip address 10.2.6.6/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Ethernet3
   no switchport
   ip address 10.3.6.6/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Ethernet4
   no switchport
   ip address 10.4.6.6/24
   ip ospf cost 10
   ip ospf network point-to-point
!
interface Loopback0
   ip address 10.0.0.6/32
!
interface Loopback1
   ip address 10.0.0.106/32
!
ip routing
!
router bgp 65000
   router-id 10.0.0.6
   no bgp default ipv4-unicast
   neighbor RRC peer group
   neighbor RRC remote-as 65000
   neighbor RRC update-source Loopback0
   neighbor RRC route-reflector-client
   neighbor RRC send-community standard extended
   neighbor 10.0.0.1 peer group RRC
   neighbor 10.0.0.2 peer group RRC
   neighbor 10.0.0.3 peer group RRC
   neighbor 10.0.0.4 peer group RRC
   !
   address-family evpn
      neighbor RRC activate
!
router ospf 1
   router-id 10.0.0.6
   network 10.0.0.0/8 area 0.0.0.0
   max-lsa 12000
!
```

**HOST-7:**

```cisco
hostname HOST-7
!
vrf definition RED
 !
 address-family ipv4
 exit-address-family
!
vrf definition WHITE
 !
 address-family ipv4
 exit-address-family
!
interface Ethernet0/0
 no shutdown
!
interface Ethernet0/0.10
 encapsulation dot1Q 10
 vrf forwarding RED
 ip address 172.16.10.7 255.255.255.0
!
interface Ethernet0/0.27
 encapsulation dot1Q 27
 ip address 172.16.27.7 255.255.255.0
!
interface Ethernet0/0.30
 encapsulation dot1Q 30
 vrf forwarding WHITE
 ip address 172.16.30.7 255.255.255.0
!
ip route 0.0.0.0 0.0.0.0 172.16.27.254
ip route vrf RED 0.0.0.0 0.0.0.0 172.16.10.1
ip route vrf WHITE 0.0.0.0 0.0.0.0 172.16.30.254
!
```

**HOST-8:**

```cisco
hostname HOST-8
!
vrf definition GRAY
 !
 address-family ipv4
 exit-address-family
!
vrf definition GREEN
 !
 address-family ipv4
 exit-address-family
!
interface Ethernet0/0
 no shutdown
!
interface Ethernet0/0.20
 encapsulation dot1Q 20
 vrf forwarding GREEN
 ip address 172.16.20.8 255.255.255.0
!
interface Ethernet0/0.40
 encapsulation dot1Q 40
 vrf forwarding GRAY
 ip address 172.16.40.8 255.255.255.0
!
interface Ethernet0/0.81
 encapsulation dot1Q 81
 ip address 172.16.81.8 255.255.255.0
!
ip route 0.0.0.0 0.0.0.0 172.16.81.254
ip route vrf GREEN 0.0.0.0 0.0.0.0 172.16.20.1
ip route vrf GRAY 0.0.0.0 0.0.0.0 172.16.40.254
!
```

**HOST-9:**

```cisco
hostname HOST-9
!
vrf definition RED
 !
 address-family ipv4
 exit-address-family
!
vrf definition WHITE
 !
 address-family ipv4
 exit-address-family
!
interface Ethernet0/0
 no shutdown
!
interface Ethernet0/0.10
 encapsulation dot1Q 10
 vrf forwarding RED
 ip address 172.16.10.9 255.255.255.0
!
interface Ethernet0/0.27
 encapsulation dot1Q 27
 ip address 172.16.27.9 255.255.255.0
!
interface Ethernet0/0.30
 encapsulation dot1Q 30
 vrf forwarding WHITE
 ip address 172.16.30.9 255.255.255.0
!
ip route 0.0.0.0 0.0.0.0 172.16.27.254
ip route vrf RED 0.0.0.0 0.0.0.0 172.16.10.2
ip route vrf WHITE 0.0.0.0 0.0.0.0 172.16.30.254
!
```

**HOST-10:**

```cisco
hostname HOST-10
!
vrf definition GRAY
 !
 address-family ipv4
 exit-address-family
!
vrf definition GREEN
 !
 address-family ipv4
 exit-address-family
!
interface Ethernet0/0
 no shutdown
!
interface Ethernet0/0.20
 encapsulation dot1Q 20
 vrf forwarding GREEN
 ip address 172.16.20.10 255.255.255.0
!
interface Ethernet0/0.40
 encapsulation dot1Q 40
 vrf forwarding GRAY
 ip address 172.16.40.10 255.255.255.0
!
interface Ethernet0/0.103
 encapsulation dot1Q 103
 ip address 172.16.103.10 255.255.255.0
!
ip route 0.0.0.0 0.0.0.0 172.16.103.254
ip route vrf GREEN 0.0.0.0 0.0.0.0 172.16.20.3
ip route vrf GRAY 0.0.0.0 0.0.0.0 172.16.40.254
!
```

**HOST-11:**

```cisco
hostname HOST-11
!
vrf definition RED
 !
 address-family ipv4
 exit-address-family
!
vrf definition WHITE
 !
 address-family ipv4
 exit-address-family
!
interface Ethernet0/0
 no shutdown
!
interface Ethernet0/0.10
 encapsulation dot1Q 10
 vrf forwarding RED
 ip address 172.16.10.11 255.255.255.0
!
interface Ethernet0/0.27
 encapsulation dot1Q 27
 ip address 172.16.27.11 255.255.255.0
!
interface Ethernet0/0.30
 encapsulation dot1Q 30
 vrf forwarding WHITE
 ip address 172.16.30.11 255.255.255.0
!
ip route 0.0.0.0 0.0.0.0 172.16.27.254
ip route vrf RED 0.0.0.0 0.0.0.0 172.16.10.4
ip route vrf WHITE 0.0.0.0 0.0.0.0 172.16.30.254
!
```

**HOST-12:**

```cisco
hostname HOST-12
!
vrf definition GRAY
 !
 address-family ipv4
 exit-address-family
!
vrf definition GREEN
 !
 address-family ipv4
 exit-address-family
!
interface Ethernet0/0
 no shutdown
!
interface Ethernet0/0.20
 encapsulation dot1Q 20
 vrf forwarding GREEN
 ip address 172.16.20.12 255.255.255.0
!
interface Ethernet0/0.40
 encapsulation dot1Q 40
 vrf forwarding GRAY
 ip address 172.16.40.12 255.255.255.0
!
interface Ethernet0/0.124
 encapsulation dot1Q 124
 ip address 172.16.124.12 255.255.255.0
!
ip route 0.0.0.0 0.0.0.0 172.16.124.254
ip route vrf GREEN 0.0.0.0 0.0.0.0 172.16.20.4
ip route vrf GRAY 0.0.0.0 0.0.0.0 172.16.40.254
!
```
