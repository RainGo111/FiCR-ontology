# FiCR Ontology

FiCR (Fire Compliance and Risk Analysis) is a domain-specific ontology for representing fire safety, fire compliance, and fire risk information in existing buildings.

- Namespace: `https://w3id.org/ficr#`
- Ontology IRI: `https://w3id.org/ficr`
- Current version: `1.0.0`
- Version IRI: `https://w3id.org/ficr/1.0.0`
- Authors: Yu Zhang, Dayou Chen, Long Chen
- License: CC BY 4.0
- Documentation: <https://raingo111.github.io/FiCR-ontology/>

## Files

- `ficr.ttl`: latest ontology source in Turtle.
- `docs/`: WIDOCO documentation for GitHub Pages.
- `docs/1.0.0/`: frozen WIDOCO documentation snapshot for version `1.0.0`.

## Regenerating Documentation

Run WIDOCO from this directory:

```powershell
java -jar .\widoco.jar -ontFile .\ficr.ttl -outFolder .\docs -rewriteAll -webVowl -lang en -getOntologyMetadata -uniteSections -includeAnnotationProperties -htaccess -noPlaceHolderText
```

After regenerating, refresh any version snapshot that should correspond to the updated ontology release.
