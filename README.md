# FiCR Ontology

FiCR (Fire Compliance and Risk Analysis) is a domain-specific ontology for representing fire safety, fire compliance, and fire risk information in existing buildings.

- Namespace: `https://w3id.org/ficr#`
- Ontology IRI: `https://w3id.org/ficr`
- Current version: `1.1.1`
- Version IRI: `https://w3id.org/ficr/1.1.1`
- Authors: Yu Zhang, Dayou Chen, Long Chen, Qiuchen Lu, Simon Sølvsten, Craig Hancock
- License: CC BY 4.0
- Documentation: <https://raingo111.github.io/FiCR-ontology/>

## Files

- `ficr.ttl`: latest ontology source in Turtle.
- `ficr_alignment/`: optional SKOS alignment module for selected external ontologies.
- `docs/`: WIDOCO documentation for GitHub Pages.
- `docs/1.0.0/`: frozen Turtle ontology snapshot for version `1.0.0`.
- `docs/1.1.0/`: frozen Turtle ontology snapshot for version `1.1.0`.
- `docs/1.1.1/`: frozen Turtle ontology snapshot for version `1.1.1`.

## Alignment Module

The alignment module is separate from the FiCR core ontology and does not change
its class or property semantics. Open
[`ficr_alignment/ficr_alignment.ttl`](ficr_alignment/ficr_alignment.ttl) in an
OWL tool to load all four alignment files through relative imports. Mapping
relations are directed from the FiCR term to the target term.

| Target ontology | Reviewed version | Mappings | Example |
|---|---:|---:|---|
| [SAREF4BLDG](ficr_alignment/ficr-align-saref4bldg.ttl) | 2.1.1 | 6 | `ficr:Sensor skos:closeMatch s4bldg:Sensor` |
| [Brick](ficr_alignment/ficr-align-brick.ttl) | 1.4.4 | 5 | `ficr:FireCompartment skos:closeMatch brick:Fire_Zone` |
| [RealEstateCore](ficr_alignment/ficr-align-rec.ttl) | 4.1.0 | 5 | `ficr:DocumentEvidence skos:broadMatch rec:Document` |
| [SOSA/SSN](ficr_alignment/ficr-align-sosa.ttl) | 2017 Recommendation | 3 | `ficr:Sensor skos:broadMatch sosa:Sensor` |

See [alignment decisions](ficr_alignment/DECISIONS.md) for mapping rationale and
the [non-alignment register](ficr_alignment/NON_ALIGNMENTS.md) for reviewed
concepts that were intentionally left unmapped.

## Regenerating Documentation

Run WIDOCO from this directory:

```powershell
java -jar .\widoco.jar -ontFile .\ficr.ttl -outFolder .\docs -rewriteAll -webVowl -lang en -getOntologyMetadata -uniteSections -includeAnnotationProperties -htaccess -noPlaceHolderText
```

After regenerating, refresh any version snapshot that should correspond to the updated ontology release.
