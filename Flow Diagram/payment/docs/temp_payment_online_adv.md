<!-- Edits:
1) line 13/14 changed the dataflow diagram png
2) line 20, changed the fourth item {{item.data}} to {{item.?}} (determined from line 957 /usr/local/lib/python3.9/site-packages/pytm/pytm.py) -->
# Threat Model Sample
***

## System Description

{tm.description}

## Dataflow Diagram

<!-- ![Level 0 DFD](dfd.png) -->
![Initial payment flow diagram](../img/payment_online.png)

## Dataflows

Name|From|To |Data|Protocol|Port
----|----|---|----|--------|----
{dataflows:repeat:{{item.name}}|{{item.source.name}}|{{item.sink.name}}|{{item.data}}|{{item.protocol}}|{{item.dstPort}}
}

## Findings

{elements:repeat:{{item.findings:if:
### {{item.name}}

{{item.findings:repeat:
**Threat**: {{{{item.id}}}} - {{{{item.description}}}}

**Severity**: {{{{item.severity}}}}

**Mitigations**: {{{{item.mitigations}}}}

**References**: {{{{item.references}}}}

}}}}}