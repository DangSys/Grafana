# We need to import Cisco Modules into generator.yml file.
# Cisco Switch and Router
  cisco:
# walk: [sysUpTime, interfaces, ifXTable]
    walk:
      - 1.3.6.1.2.1.2.2.1.1
      - 1.3.6.1.2.1.2.2.1.2
      - 1.3.6.1.2.1.2.2.1.10
      - 1.3.6.1.2.1.2.2.1.13
      - 1.3.6.1.2.1.2.2.1.14
      - 1.3.6.1.2.1.2.2.1.16
      - 1.3.6.1.2.1.2.2.1.19
      - 1.3.6.1.2.1.2.2.1.2
      - 1.3.6.1.2.1.2.2.1.20
      - 1.3.6.1.2.1.2.2.1.5
      - 1.3.6.1.2.1.2.2.1.7
      - 1.3.6.1.2.1.2.2.1.8
      - 1.3.6.1.2.1.31.1.1.1.1
      - 1.3.6.1.2.1.31.1.1.1.18
#      - 1.3.6.1.4.1.9.9.48.1.1.1.5
#      - 1.3.6.1.4.1.9.9.48.1.1.1.6
#      - 1.3.6.1.4.1.9.2.1
      - 1.3.6.1.2.1.1.5
    lookups:
      - source_indexes: [ifIndex]
        lookup: ifAlias
      - source_indexes: [ifIndex]
        lookup: ifDescr
      - source_indexes: [ifIndex]
       # Use OID to avoid conflict with Netscaler NS-ROOT-MIB.
        lookup: 1.3.6.1.2.1.31.1.1.1.1 # ifName
    overrides:
      ifAlias:
        ignore: true # Lookup metric
      ifDescr:
        ignore: true # Lookup metric
      ifName:
        ignore: true # Lookup metric
      ifType:
        type: EnumAsInfo
    max_repetitions: 25
    retries: 3
    timeout: 10s
