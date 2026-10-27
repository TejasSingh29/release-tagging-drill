# Tag History Audit

## Objective

The repository contains inconsistent release tags, making it difficult to identify deployed versions, audit changes, and choose a reliable rollback target.

## Findings

### 1. Inconsistent version naming — `version-1.0`

**Evidence:** The tag uses the `version-` prefix instead of the standard `vMAJOR.MINOR.PATCH` format.

**Impact:** Developers cannot rely on one predictable naming convention when searching or sorting releases.

**Risk:** Automated release discovery and manual rollback selection may overlook this tag or treat it inconsistently.

**Recommendation:** Use semantic version tags such as `v1.0.0`.

### 2. Missing version prefix — `1.5.0`

**Evidence:** The tag does not include the required `v` prefix.

**Impact:** The tag does not follow the same naming pattern as the proposed release convention.

**Risk:** Release lists become inconsistent, and scripts or deployment documentation expecting the standard prefix may miss this release.

**Recommendation:** Standardize all new production tags as `vMAJOR.MINOR.PATCH`.

### 3. Non-semantic release name — `release_2`

**Evidence:** The tag uses a generic release label without a major, minor, or patch version.

**Impact:** The team cannot determine the release's position in the version sequence from its name alone.

**Risk:** Selecting a previous known-good release becomes harder, particularly during a production incident.

**Recommendation:** Assign a meaningful semantic version based on the changes shipped.

### 4. Ambiguous final-release name — `v2-final-FINAL`

**Evidence:** The tag uses repeated `final` wording instead of a standard version number.

**Impact:** It is unclear whether this is the actual final release, a replacement, or an abandoned release candidate.

**Risk:** A team may deploy or roll back to the wrong commit because the tag's meaning is ambiguous.

**Recommendation:** Use a stable version such as `v2.0.0`, and reserve pre-release identifiers for candidates such as `v2.0.0-rc.1`.

### 5. Incomplete semantic version — `v1.4.2`

**Evidence:** Although this tag follows the three-part version format, its name alone does not establish whether it was created as an annotated release tag or whether it matches a documented deployment.

**Impact:** A syntactically valid tag is not sufficient deployment evidence without a commit, release message, and deployment record.

**Risk:** Incident responders may identify the version name but still lack evidence that it corresponds to the deployed build.

**Recommendation:** Verify its tag type and target commit, then document the commit and deployment details in `RELEASE-MAP.md`.

## Conclusion

The repository needs one naming convention, annotated production tags, meaningful release messages, and a release map linking each version to its exact commit and deployment record. All new releases should follow the same policy to make rollbacks reproducible and audits easier.
