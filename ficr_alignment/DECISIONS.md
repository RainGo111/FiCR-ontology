# FiCR v1.1.1 Alignment Candidate Decisions

Status: approved and finalised after the single mapping review checkpoint

This module is class-to-class only. It contains no property, instance, or
`owl:equivalentClass` mapping. The relation is read from the FiCR term to the
target term. Therefore `skos:broadMatch` means that the target term is broader,
and `skos:narrowMatch` means that the target term is narrower.

No candidate currently satisfies both strict class entailment and the
side-effect safety gate for `rdfs:subClassOf`. All candidates therefore remain
SKOS mappings. This follows the domain and range inference risk identified by
Schneider (2017), while applying the stricter project rules in preference to
the paper's original equivalence mappings.

## Prefixes

| Prefix | Namespace |
|---|---|
| `ficr:` | `https://w3id.org/ficr#` |
| `s4bldg:` | `https://saref.etsi.org/saref4bldg/` |
| `brick:` | `https://brickschema.org/schema/Brick#` |
| `rec:` | `https://w3id.org/rec#` |
| `sosa:` | `http://www.w3.org/ns/sosa/` |
| `ssn:` | `http://www.w3.org/ns/ssn/` |

## SAREF4BLDG 2.1.1

Candidate count: 6

| FiCR term | Target term | Relation | One-line justification | Stronger relation rejected and why |
|---|---|---|---|---|
| `ficr:RoomSpace` | `s4bldg:BuildingSpace` | `skos:broadMatch` | A FiCR room is an enclosed non-circulation building space, while SAREF4BLDG covers building spaces generally. | Subclass and equivalence are rejected because the target also covers circulation, cavity, and other non-room spaces. |
| `ficr:Equipment` | `s4bldg:BuildingDevice` | `skos:closeMatch` | Both describe identifiable physical devices or apparatus used to perform tasks in a building. | Subclass and equivalence are rejected because FiCR adds maintainability and topology criteria, while SAREF4BLDG adds its own device and building-object semantics. |
| `ficr:Alarm` | `s4bldg:Alarm` | `skos:broadMatch` | FiCR models an equipment-level fire alarm, while SAREF4BLDG models alarms for any abnormal condition. | Subclass and equivalence are rejected because the target is not restricted to fire warning equipment. |
| `ficr:Sensor` | `s4bldg:Sensor` | `skos:closeMatch` | Both classes describe a physical building sensor that detects or measures environmental conditions and produces a signal. | Equivalence and subclass are rejected because the measurement and distribution-control commitments differ between the two models. |
| `ficr:Controller` | `s4bldg:Controller` | `skos:broadMatch` | Both represent building automation controllers, but SAREF4BLDG explicitly permits physical or virtual controllers. | Subclass and equivalence are rejected because FiCR places controllers under physical equipment, while the target also admits virtual controllers. |
| `ficr:FireAndSmokeDamper` | `s4bldg:Damper` | `skos:broadMatch` | A FiCR fire-and-smoke damper is a fire-specific subtype of the generic airflow damper described by SAREF4BLDG. | Subclass and equivalence are rejected because SAREF4BLDG dampers are generic HVAC flow controllers without fire or smoke performance semantics. |

No observation or evidence mapping is proposed for this target. SAREF Core
models an observation as an executed procedure, while FiCR evidence classes
model assessment-supporting artifacts or content. Treating those as the same
class would cross the activity and artifact boundary.

## Brick 1.4.4

Candidate count: 5

| FiCR term | Target term | Relation | One-line justification | Stronger relation rejected and why |
|---|---|---|---|---|
| `ficr:RoomSpace` | `brick:Room` | `skos:closeMatch` | Both represent bounded building spaces understood as rooms rather than arbitrary locations; their extensions overlap, but neither contains the other because their room boundary and inclusion criteria differ. | Equivalence and subclass are rejected because FiCR explicitly includes cupboards, warehouses, and auditoria and excludes circulation and cavities, while Brick supplies only a room taxonomy base. |
| `ficr:FireCompartment` | `brick:Fire_Zone` | `skos:closeMatch` | Both partition a building for fire-related management, but FiCR uses physical fire-resisting boundaries and Brick uses a logical monitored zone. | Any subsumption or equivalence is rejected because physical compartmentation and monitoring-zone membership are different classification criteria. |
| `ficr:FireProtectionEquipment` | `brick:Fire_Safety_Equipment` | `skos:closeMatch` | Both collect maintainable equipment used for fire detection, warning, suppression, control, or related protection. | Subclass and equivalence are rejected because neither ontology establishes strict identity of the category boundary. |
| `ficr:FireProtectionSystem` | `brick:Fire_Safety_System` | `skos:narrowMatch` | Brick limits the target system to monitoring, detection, and suppression, while FiCR also includes smoke control, emergency lighting, protected supply, firefighting, and evacuation support. | Subclass and equivalence are rejected because the target covers only part of the FiCR system-level provision scope. |
| `ficr:Alarm` | `brick:Fire_Alarm` | `skos:closeMatch` | Both denote equipment-level fire alarm items rather than a complete fire alarm system. | Equivalence and subclass are rejected because Brick provides only hierarchy placement and does not state FiCR's warning-function and arrangement criteria. |

`brick:Sensor` is not mapped to `ficr:Sensor`. Brick models `Sensor` as an
input point, while FiCR models a physical equipment item. This is an important
non-alignment rather than a lexical match.

## RealEstateCore 4.1.0

Candidate count: 5

| FiCR term | Target term | Relation | One-line justification | Stronger relation rejected and why |
|---|---|---|---|---|
| `ficr:RoomSpace` | `rec:Room` | `skos:closeMatch` | Both identify room-scale architectural spaces within a building. | Equivalence and subclass are rejected because REC does not state the FiCR exclusions for circulation and cavity spaces or its expanded room examples. |
| `ficr:GroundAndAboveStorey` | `rec:Level` | `skos:broadMatch` | A ground or above-ground FiCR storey is one kind of the generic building level represented by REC. | Subclass and equivalence are rejected because REC Level also includes basement and other levels without FiCR's elevation classification. |
| `ficr:BasementStorey` | `rec:Level` | `skos:broadMatch` | A FiCR basement storey is one kind of the generic building level represented by REC. | Subclass and equivalence are rejected because REC Level does not carry FiCR's below-ground threshold or sloping-site interpretation. |
| `ficr:Sensor` | `rec:SensorEquipment` | `skos:closeMatch` | Both describe physical sensor equipment deployed as part of building ICT or control infrastructure. | Equivalence and subclass are rejected because REC places sensors under ICT and imported Brick equipment semantics, while FiCR uses a direct physical-equipment model. |
| `ficr:DocumentEvidence` | `rec:Document` | `skos:broadMatch` | FiCR document evidence is a document used to support an assessment, while REC represents documents without requiring an evidential role. | Subclass and equivalence are rejected because the target includes documents that are not assessment evidence. |

Both FiCR storey subclasses are intentionally retained. REC aggregates them as
`rec:Level`, so the FiCR ground/basement distinction is not preserved by these
mappings.

REC-native fire equipment mappings are not proposed. Those concepts are
supplied through REC's imported Brick graph and are already reviewed in the
independent Brick alignment.

## SOSA/SSN 2017 Recommendation

Candidate count: 3

| FiCR term | Target term | Relation | One-line justification | Stronger relation rejected and why |
|---|---|---|---|---|
| `ficr:Sensor` | `sosa:Sensor` | `skos:broadMatch` | A FiCR building sensor is a physical-device case of SOSA Sensor, which also permits human agents and software simulations. | Subclass and equivalence are rejected because the target is role-based and includes non-physical sensors. |
| `ficr:ObservedEvidence` | `sosa:Result` | `skos:broadMatch` | FiCR observed evidence is an assessment-oriented subset of the generic observation, actuation, or sampling outputs represented by SOSA Result. | Subclass and equivalence are rejected because SOSA Result does not require an evidential role and includes outputs outside observation-based assessment. |
| `ficr:SensorEvidence` | `sosa:Result` | `skos:broadMatch` | FiCR sensor evidence is a sensor-generated assessment artifact within the broader class of procedure results represented by SOSA. | Subclass and equivalence are rejected because FiCR classifies by assessment provenance and use, whereas SOSA also includes non-evidential procedure outcomes. |

No FiCR space or zone mapping is proposed for SOSA/SSN. A
`sosa:FeatureOfInterest` is an observation-relative role and is not a class of
building space, element, or physical object.

No mapping is retained between `ficr:BuildingSystem` and `ssn:System`. SSN
classifies systems by implementation of procedures, while FiCR classifies them
as interconnected building infrastructure. Neither extension contains the
other, so broad, narrow, and close mapping relations would all overstate the
correspondence.
