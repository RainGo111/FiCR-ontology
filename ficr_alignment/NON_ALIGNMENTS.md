# FiCR v1.1.1 Non-Alignment Register

This register records reviewed FiCR classes for which no defensible mapping was
encoded. Absence is an explicit finding. It is not a coverage failure.

## Cross-target evidence finding

All four target families contain observation, event, measurement, or result
semantics, but none represents evidence as an assessment artifact with FiCR's
supporting, status, and traceability role. REC `Document` is retained only as a
broader match for document evidence. SOSA `Result` is retained only as a broader
match for observed and sensor evidence, and therefore does not preserve the
evidential role. This activity/event versus assessment-artifact boundary is the
main cross-target evidence non-alignment.

## Compliance, evidence, and risk concepts

| FiCR term | Target scope | Reason for non-alignment |
|---|---|---|
| `ficr:RegulatoryRequirement` | All four targets | None provides a class for a fire-regulatory criterion with FiCR's applicability, required-value, and assessment traceability role. |
| `ficr:RegulatoryInstrument` | All four targets | Generic document concepts do not preserve the legal or regulatory instrument identity required by FiCR. |
| `ficr:RegulatorySource` | All four targets | No target models a regulatory source as an assessment evidence source with FiCR's provenance role. |
| `ficr:RequirementSpecification` | All four targets | No target models a requirement specification as the structured criterion consumed by compliance checking. |
| `ficr:ComplianceFinding` | All four targets | Observation and event classes do not represent a finding that binds an assessed item, requirement, result, and evidence status. |
| `ficr:ComplianceResult` | All four targets | Generic states and results do not preserve FiCR's controlled compliant, non-compliant, and undetermined assessment semantics. |
| `ficr:AssessmentFinding` | All four targets | No target has an assessment finding record with FiCR's assessed-target and supporting-evidence traceability. |
| `ficr:EvidenceStatus` | All four targets | None provides FiCR's controlled available, insufficient, missing, and not-required evidence states. |
| `ficr:EvidenceItem` | All four targets | Target observation and result classes classify activities or outputs, not evidence artifacts used to justify an assessment. |
| `ficr:ObservedEvidence` | SAREF4BLDG, Brick, REC | SAREF Observation and REC ObservationEvent are activities or events, Brick has no evidence model, and none preserves the assessment-artifact identity. |
| `ficr:SensorEvidence` | SAREF4BLDG, Brick, REC | A sensor-generated evidence artifact has different identity and lifecycle criteria from an observation activity, event, point, or signal. |
| `ficr:TestEvidence` | All four targets | A test evidence artifact is not identical to a measurement activity or generic result, and the evidential role would be lost. |
| `ficr:BoundaryConditionRecord` | All four targets | No target models an assessed or assumed fire-boundary condition with evidence and condition-state links. |
| `ficr:BoundaryAssumption` | All four targets | No target represents a provisional boundary-performance assumption used as a risk-analysis dependency. |
| `ficr:BoundaryPerformanceAspect` | All four targets | Generic properties do not encode FiCR's controlled fire-boundary performance dimensions. |
| `ficr:RiskAnalysis` | All four targets | No target models a fire-risk assessment that produces traceable risk findings from evidence and scenarios. |
| `ficr:RiskFinding` | All four targets | Generic events and results do not represent FiCR's inspection-prioritisation finding record. |
| `ficr:RiskUnit` | All four targets | Space and zone classes do not capture an assessment-defined aggregation unit used for risk interpretation and prioritisation. |
| `ficr:FireRiskScenario` | All four targets | No target provides the scenario construct used to contextualise FiCR risk findings and assumptions. |
| `ficr:FireRiskAssessmentTask` | All four targets | Procedure and task concepts do not preserve FiCR's executable O&M risk-assessment work-item semantics. |

## Reviewed lexical and modelling mismatches

| FiCR term | Rejected target term | Reason for non-alignment |
|---|---|---|
| `ficr:Sensor` | `brick:Sensor` | Brick models an input point, while FiCR models a physical equipment item; the lexical match is an ontological mismatch. |
| `ficr:FireCompartment` | `rec:Zone` | REC Zone has no physical fire-resisting boundary criterion and includes unrelated technology- and use-defined zones. |
| `ficr:SensorEvidence` | `rec:ObservationEvent` | An evidence artifact and a temporally indexed point event have different identity and lifecycle criteria. |
| `ficr:PhysicalObject` | `sosa:FeatureOfInterest` | SOSA FeatureOfInterest is an observation-relative role rather than a material-object category. |
| `ficr:BuildingSystem` | `ssn:System` | SSN classifies systems by implementation of procedures, while FiCR classifies interconnected building infrastructure; neither extension contains the other. |
| `ficr:FireSprinklerSystem` | `s4bldg:FireSuppressionTerminal` | FiCR models a distributed suppression system, while SAREF4BLDG models an individual fluid-delivery terminal. |

## FiCR fabric-element vocabulary

The following declared descendants of `ficr:FabricElement` were checked against
the four targets. Generic `BuildingObject`, `Equipment`, `Location`, or `Asset`
classes are not treated as useful counterparts for a specific fabric element.

| FiCR term | Target scope | Reason for non-alignment or deliberate omission |
|---|---|---|
| `ficr:Beam` | All four targets | No target provides a class for a structural beam as a building fabric element. |
| `ficr:CavityBarrier` | All four targets | No target represents a cavity-closing fire barrier with smoke and flame restriction semantics. |
| `ficr:Ceiling` | All four targets | No target provides the corresponding building fabric surface class. |
| `ficr:Cladding` | All four targets | No target represents external cladding as a fire-relevant fabric element. |
| `ficr:Closing` | All four targets | No target provides FiCR's common category for doors, windows, and dampers that close openings. |
| `ficr:Column` | All four targets | No target provides a structural-column fabric class. |
| `ficr:CompartmentFloor` | All four targets | No target represents a fire-resisting floor that separates fire compartments. |
| `ficr:CompartmentWall` | All four targets | No target represents a fire-resisting wall that separates fire compartments. |
| `ficr:Curtain` | All four targets | No target provides the corresponding movable fabric or shading component with FiCR's meaning. |
| `ficr:Doorset` | All four targets | No target represents the complete integrated door leaf, frame, and hardware assembly. |
| `ficr:ExternalWall` | All four targets | No target provides the corresponding external-wall fabric class in the reviewed versions. |
| `ficr:ExternalWallDoor` | All four targets | No target represents a doorset specifically located in an external wall. |
| `ficr:ExternalWallWindow` | All four targets | No target represents a window specifically located in an external wall. |
| `ficr:FireAndSmokeDamper` | Brick, REC, SOSA/SSN | No counterpart is present in these targets; the SAREF4BLDG generic Damper mapping is recorded separately. |
| `ficr:FireDamper` | All four targets | SAREF4BLDG only provides a generic HVAC damper, and the more specific FiCR fire-and-smoke damper was selected as the single curated anchor. |
| `ficr:FireDoorset` | All four targets | No target represents a doorset with fire-resistance and closure performance semantics. |
| `ficr:FireStop` | All four targets | No target represents a fire-stopping product or installation at penetrations and joints. |
| `ficr:Floor` | All four targets | Brick Floor and REC Level are spatial levels, not a physical floor fabric element. |
| `ficr:FloorSlab` | All four targets | No target provides a physical floor-slab fabric class. |
| `ficr:Opening` | All four targets | No target provides a fabric opening class with FiCR's building-element role. |
| `ficr:ProtectedStairway` | All four targets | Spatial stair or level concepts do not represent a fire-protected stairway fabric assembly. |
| `ficr:Railing` | All four targets | No target provides the corresponding guard or railing fabric class. |
| `ficr:Roof` | All four targets | No target provides the corresponding roof fabric class in the reviewed versions. |
| `ficr:RoofSlab` | All four targets | No target provides a roof-slab structural fabric class. |
| `ficr:Rooflight` | All four targets | No target represents a rooflight as a complete fabric element. |
| `ficr:RooflightOpening` | All four targets | No target represents the opening occupied by a rooflight. |
| `ficr:SelfClosingDevice` | All four targets | Generic actuators do not preserve the door-specific self-closing fire-safety function. |
| `ficr:Slab` | All four targets | No target provides the corresponding structural slab fabric class. |
| `ficr:SolarShadingDevice` | All targets | SAREF4BLDG has a functional shading device, but this non-fire fabric mapping is outside the approved anchor scope. |
| `ficr:SpecifiedAttachment` | All four targets | No target represents an attachment whose fire-relevant specification is tracked as a fabric element. |
| `ficr:Stair` | All four targets | No target provides a physical stair assembly class distinct from spatial levels and rooms. |
| `ficr:StairFlight` | All four targets | No target provides a stair-flight fabric class. |
| `ficr:StructuralElement` | All four targets | Generic equipment or asset classes do not represent the load-bearing fabric category. |
| `ficr:Wall` | All four targets | No target provides the corresponding physical wall fabric class in the reviewed versions. |
| `ficr:WallFoundation` | All four targets | No target provides a wall-foundation structural fabric class. |
| `ficr:Window` | All four targets | No target represents FiCR's physical window fabric element in the reviewed versions. |
