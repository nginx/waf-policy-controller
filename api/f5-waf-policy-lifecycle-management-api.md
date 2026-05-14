## Overview
F5 WAF Policy Lifecycle Management API Reference

# API Reference

## Packages
- [appprotect.f5.com/v1](#appprotectf5comv1)


## appprotect.f5.com/v1

Package v1 contains API Schema definitions for the appprotect v1 API group

### Resource Types
- [APLogConf](#aplogconf)
- [APLogConfList](#aplogconflist)
- [APPolicy](#appolicy)
- [APPolicyList](#appolicylist)
- [APSignatures](#apsignatures)
- [APSignaturesList](#apsignatureslist)
- [APUserSig](#apusersig)
- [APUserSigList](#apusersiglist)



#### APLogConf



APLogConf is the Schema for the aplogconfs API



_Appears in:_
- [APLogConfList](#aplogconflist)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `apiVersion` _string_ | `appprotect.f5.com/v1` | | |
| `kind` _string_ | `APLogConf` | | |
| `metadata` _[ObjectMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#objectmeta-v1-meta)_ | Refer to Kubernetes API documentation for fields of `metadata`. |  |  |
| `spec` _[APLogConfSpec](#aplogconfspec)_ |  |  |  |
| `status` _[APLogConfStatus](#aplogconfstatus)_ |  |  |  |


#### APLogConfList



APLogConfList contains a list of APLogConf





| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `apiVersion` _string_ | `appprotect.f5.com/v1` | | |
| `kind` _string_ | `APLogConfList` | | |
| `metadata` _[ListMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#listmeta-v1-meta)_ | Refer to Kubernetes API documentation for fields of `metadata`. |  |  |
| `items` _[APLogConf](#aplogconf) array_ |  |  |  |


#### APLogConfSpec



APLogConfSpec defines the desired state of APLogConf



_Appears in:_
- [APLogConf](#aplogconf)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `content` _[LogConfContent](#logconfcontent)_ |  |  |  |
| `filter` _[LogConfFilter](#logconffilter)_ |  |  |  |


#### APLogConfStatus



APLogConfStatus defines the observed state of LogConf



_Appears in:_
- [APLogConf](#aplogconf)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `bundle` _[BundleStatus](#bundlestatus)_ | Bundle holds the “ready/pending/invalid” bundle info |  | Optional: \{\} <br /> |
| `processing` _[ProcessingStatus](#processingstatus)_ | Processing holds the compiler/validation metadata |  | Optional: \{\} <br /> |
| `observedGeneration` _integer_ | ObservedGeneration is the most recent metadata.generation for which the<br />controller successfully processed this APLogConf resource.<br />This field tracks the Kubernetes metadata.generation to determine if<br />the resource needs reprocessing when the spec changes. |  | Optional: \{\} <br /> |
| `inProgressGeneration` _integer_ | InProgressGeneration records the metadata.generation for which a<br />compilation job is currently pending or processing |  |  |
| `previousBundleLocation` _string_ | PreviousBundleLocation stores the S3 location of the previous (N-1) bundle.<br />When a new bundle is compiled, the old bundle is NOT deleted immediately<br />because traffic nodes may still be fetching it. Instead, the old location<br />is saved here. On the NEXT successful compilation, the bundle at this<br />location (now N-2) is deleted, and the current bundle location takes its place. |  | Optional: \{\} <br /> |


#### APPolicy



APPolicy is the Schema for the APPolicy API

_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyList](#appolicylist)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `apiVersion` _string_ | `appprotect.f5.com/v1` | | |
| `kind` _string_ | `APPolicy` | | |
| `metadata` _[ObjectMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#objectmeta-v1-meta)_ | Refer to Kubernetes API documentation for fields of `metadata`. |  |  |
| `spec` _[APPolicySpec](#appolicyspec)_ |  |  |  |
| `status` _[APPolicyStatus](#appolicystatus)_ |  |  | XPreserveUnknownFields: \{\} <br /> |


#### APPolicyAnomalies





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyMitigations](#appolicymitigations)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `action` _string_ |  |  |  |
| `name` _string_ |  |  |  |
| `scoreThreshold` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |


#### APPolicyAttackType

_Underlying type:_ _[struct{Name *string "json:\"name,omitempty\""}](#struct{name-*string-"json:\"name,omitempty\""})_



_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicySignatureSetFilter](#appolicysignaturesetfilter)



#### APPolicyBlockingSettings





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `violations` _[APPolicyViolations](#appolicyviolations) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `evasions` _[APPolicyEvasions](#appolicyevasions) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `http-protocols` _[APPolicyHttpprotocols](#appolicyhttpprotocols) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |


#### APPolicyBotDefense





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `mitigations` _[APPolicyMitigations](#appolicymitigations)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `settings` _[APPolicySettings](#appolicysettings)_ |  |  | XPreserveUnknownFields: \{\} <br /> |


#### APPolicyBrowserDefinitions





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `name` _string_ |  |  |  |
| `isUserDefined` _boolean_ |  |  |  |
| `matchRegex` _string_ |  |  |  |
| `matchString` _string_ |  |  |  |


#### APPolicyBrowsers





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyMitigations](#appolicymitigations)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `action` _string_ |  |  |  |
| `maxVersion` _integer_ |  |  | Maximum: 2.147483647e+09 <br />Minimum: 0 <br /> |
| `minVersion` _integer_ |  |  | Maximum: 2.147483647e+09 <br />Minimum: 0 <br /> |
| `name` _string_ |  |  |  |


#### APPolicyBundleStatus



APPolicyBundleStatus reports on the actual bundle tar-ball, its state and embedded signatures.

_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyStatus](#appolicystatus)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `state` _[BundleState](#bundlestate)_ | State is the current bundle state (pending, processing, ready, invalid) |  | Enum: [pending processing ready invalid] <br /> |
| `location` _string_ | Location is the path/URL where the compiled bundle is stored; only set when State == “ready” |  | Optional: \{\} <br /> |
| `sha256` _string_ | Sha256 is the SHA256 hash of the bundle file |  | Optional: \{\} <br /> |
| `compilerVersion` _string_ | CompilerVersion is the version of the compiler used to build this bundle. |  | Optional: \{\} <br /> |
| `signatures` _[BundleSignatures](#bundlesignatures)_ | Signatures holds the revisions of embedded signature files – only if this is a policy bundle. |  | XPreserveUnknownFields: \{\} <br />Optional: \{\} <br /> |
| `observedGeneration` _integer_ | ObservedGeneration is the metadata.generation of the APPolicy resource<br />that was used to produce this policy bundle.<br />This tracks which version of the policy spec generated the current bundle. |  | Optional: \{\} <br /> |


#### APPolicyCharacterSet





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyCharacterSets](#appolicycharactersets)
- [APPolicyGraphqlProfiles](#appolicygraphqlprofiles)
- [APPolicyJsonProfiles](#appolicyjsonprofiles)
- [APPolicyParameters](#appolicyparameters)
- [APPolicyUrls](#appolicyurls)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `isAllowed` _boolean_ |  |  |  |
| `metachar` _string_ |  |  |  |


#### APPolicyCharacterSets





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `characterSet` _[APPolicyCharacterSet](#appolicycharacterset) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `characterSetType` _string_ |  |  |  |


#### APPolicyClasses





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyMitigations](#appolicymitigations)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `action` _string_ |  |  |  |
| `name` _string_ |  |  |  |


#### APPolicyContentProfile





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyParameters](#appolicyparameters)
- [APPolicyUrlContentProfiles](#appolicyurlcontentprofiles)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `name` _string_ |  |  |  |


#### APPolicyCookieSettings





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `maximumCookieHeaderLength` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |


#### APPolicyCookies





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `accessibleOnlyThroughTheHttpProtocol` _boolean_ |  |  |  |
| `securedOverHttpsConnection` _boolean_ |  |  |  |
| `name` _string_ |  |  |  |
| `enforcementType` _string_ |  |  |  |
| `attackSignaturesCheck` _boolean_ |  |  |  |
| `insertSameSiteAttribute` _string_ |  |  |  |
| `maskValueInLogs` _boolean_ |  |  |  |
| `signatureOverrides` _[APPolicySignatureOverrides](#appolicysignatureoverrides) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `type` _string_ |  |  |  |
| `decodeValueAsBase64` _string_ |  |  |  |
| `wildcardOrder` _integer_ |  |  |  |


#### APPolicyCrossDomainAllowedOrigin





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyHtml5CrossOriginRequestsEnforcement](#appolicyhtml5crossoriginrequestsenforcement)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `includeSubDomains` _boolean_ |  |  |  |
| `originName` _string_ |  |  |  |
| `originPort` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `originProtocol` _string_ |  |  |  |


#### APPolicyCsrfProtection





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `enabled` _boolean_ |  |  |  |
| `expirationTimeInSeconds` _string_ |  |  | Pattern: `disabled\|\d+` <br /> |
| `sslOnly` _boolean_ |  |  |  |


#### APPolicyCsrfUrls





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `enforcementAction` _string_ |  |  |  |
| `method` _string_ |  |  |  |
| `url` _string_ |  |  |  |
| `wildcardOrder` _integer_ |  |  |  |


#### APPolicyDataGuard





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `enabled` _boolean_ |  |  |  |
| `maskData` _boolean_ |  |  |  |
| `usSocialSecurityNumbers` _boolean_ |  |  |  |
| `creditCardNumbers` _boolean_ |  |  |  |
| `customPatterns` _boolean_ |  |  |  |
| `enforcementMode` _string_ |  |  |  |
| `enforcementUrls` _string array_ |  |  |  |
| `lastCcnDigitsToExpose` _integer_ |  |  |  |
| `lastSsnDigitsToExpose` _integer_ |  |  |  |
| `firstCustomCharactersToExpose` _integer_ |  |  |  |
| `lastCustomCharactersToExpose` _integer_ |  |  |  |
| `customPatternsList` _string array_ |  |  |  |


#### APPolicyDisallowedGeolocationReference





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `link` _string_ |  |  | Pattern: `^http` <br /> |


#### APPolicyEnforcerSettings





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `enforcerStateCookies` _[APPolicyEnforcerStateCookies](#appolicyenforcerstatecookies)_ |  |  | XPreserveUnknownFields: \{\} <br /> |


#### APPolicyEnforcerStateCookies





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyEnforcerSettings](#appolicyenforcersettings)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `httpOnlyAttribute` _boolean_ |  |  |  |
| `sameSiteAttribute` _string_ |  |  |  |
| `secureAttribute` _string_ |  |  |  |


#### APPolicyEntity





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyModifications](#appolicymodifications)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `name` _string_ |  |  |  |


#### APPolicyEntityChanges





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyModifications](#appolicymodifications)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `type` _string_ |  |  |  |


#### APPolicyEvasions





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyBlockingSettings](#appolicyblockingsettings)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `description` _string_ |  |  |  |
| `enabled` _boolean_ |  |  |  |
| `maxDecodingPasses` _integer_ |  |  |  |


#### APPolicyExternalAuthentication



APPolicyExternalAuthentication defines authentication for Git repositories

_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyExternalReferenceDetails](#appolicyexternalreferencedetails)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `token` _string_ | Token for authentication (contains the name of the Kubernetes secret) |  | Optional: \{\} <br /> |


#### APPolicyExternalReferenceDetails



APPolicyExternalReferenceDetails contains configuration for Git repository references

_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `repositoryDetails` _[APPolicyRepositoryDetails](#appolicyrepositorydetails)_ | Repository details for Git repositories<br />Required when $ref points to a Git repository, optional for HTTPS URLs |  | XPreserveUnknownFields: \{\} <br />Optional: \{\} <br /> |
| `authentication` _[APPolicyExternalAuthentication](#appolicyexternalauthentication)_ | Authentication configuration for accessing Git repositories |  | XPreserveUnknownFields: \{\} <br />Optional: \{\} <br /> |


#### APPolicyFiletypes





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `name` _string_ |  |  |  |
| `type` _string_ |  |  |  |
| `$action` _string_ |  |  |  |
| `allowed` _boolean_ |  |  |  |
| `checkPostDataLength` _boolean_ |  |  |  |
| `postDataLength` _integer_ |  |  |  |
| `checkRequestLength` _boolean_ |  |  |  |
| `requestLength` _integer_ |  |  |  |
| `checkUrlLength` _boolean_ |  |  |  |
| `urlLength` _integer_ |  |  |  |
| `checkQueryStringLength` _boolean_ |  |  |  |
| `queryStringLength` _integer_ |  |  |  |
| `responseCheck` _boolean_ |  |  |  |
| `wildcardOrder` _integer_ |  |  |  |


#### APPolicyFilterAccuracyFilter

_Underlying type:_ _string_





_Appears in:_
- [APPolicySignatureSetFilter](#appolicysignaturesetfilter)

| Field | Description |
| --- | --- |
| `all` |  |
| `eq` |  |
| `ge` |  |
| `le` |  |


#### APPolicyFilterAccuracyValue

_Underlying type:_ _string_





_Appears in:_
- [APPolicySignatureSetFilter](#appolicysignaturesetfilter)

| Field | Description |
| --- | --- |
| `high` |  |
| `low` |  |
| `medium` |  |


#### APPolicyFilterHasCve

_Underlying type:_ _string_





_Appears in:_
- [APPolicySignatureSetFilter](#appolicysignaturesetfilter)

| Field | Description |
| --- | --- |
| `all` |  |
| `false` |  |
| `true` |  |


#### APPolicyFilterLastUpdatedFilter

_Underlying type:_ _string_





_Appears in:_
- [APPolicySignatureSetFilter](#appolicysignaturesetfilter)

| Field | Description |
| --- | --- |
| `all` |  |
| `eq` |  |
| `ge` |  |
| `le` |  |


#### APPolicyFilterRiskFilter

_Underlying type:_ _string_





_Appears in:_
- [APPolicySignatureSetFilter](#appolicysignaturesetfilter)

| Field | Description |
| --- | --- |
| `all` |  |
| `eq` |  |
| `ge` |  |
| `le` |  |


#### APPolicyFilterRiskValue

_Underlying type:_ _string_





_Appears in:_
- [APPolicySignatureSetFilter](#appolicysignaturesetfilter)

| Field | Description |
| --- | --- |
| `high` |  |
| `low` |  |
| `medium` |  |


#### APPolicyFilterSignatureType

_Underlying type:_ _string_





_Appears in:_
- [APPolicySignatureSetFilter](#appolicysignaturesetfilter)

| Field | Description |
| --- | --- |
| `all` |  |
| `request` |  |
| `response` |  |


#### APPolicyFilterTagFilter

_Underlying type:_ _string_





_Appears in:_
- [APPolicySignatureSetFilter](#appolicysignaturesetfilter)

| Field | Description |
| --- | --- |
| `all` |  |
| `eq` |  |
| `untagged` |  |


#### APPolicyFilterUserDefinedFilter

_Underlying type:_ _string_





_Appears in:_
- [APPolicySignatureSetFilter](#appolicysignaturesetfilter)

| Field | Description |
| --- | --- |
| `all` |  |
| `false` |  |
| `true` |  |


#### APPolicyGeneral





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `allowedResponseCodes` _[APPolicyResponseCode](#appolicyresponsecode) array_ |  |  | Maximum: 999 <br />Minimum: 100 <br /> |
| `customXffHeaders` _string array_ |  |  |  |
| `trustXff` _boolean_ |  |  |  |
| `maskCreditCardNumbersInRequest` _boolean_ |  |  |  |


#### APPolicyGraphqlDefenseAttributes





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyGraphqlProfiles](#appolicygraphqlprofiles)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `allowIntrospectionQueries` _boolean_ |  |  |  |
| `maximumBatchedQueries` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `maximumQueryCost` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `maximumStructureDepth` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `maximumTotalLength` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `maximumValueLength` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `tolerateParsingWarnings` _boolean_ |  |  |  |


#### APPolicyGraphqlProfiles





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `name` _string_ |  |  |  |
| `$action` _string_ |  |  |  |
| `attackSignaturesCheck` _boolean_ |  |  |  |
| `defenseAttributes` _[APPolicyGraphqlDefenseAttributes](#appolicygraphqldefenseattributes)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `description` _string_ |  |  |  |
| `metacharElementCheck` _boolean_ |  |  |  |
| `metacharOverrides` _[APPolicyCharacterSet](#appolicycharacterset) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `responseEnforcement` _[APPolicyResponseEnforcement](#appolicyresponseenforcement)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `signatureOverrides` _[APPolicySignatureOverrides](#appolicysignatureoverrides) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `sensitiveData` _[APPolicySensitiveData](#appolicysensitivedata) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |


#### APPolicyGrpcDefenseAttributes





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyGrpcProfiles](#appolicygrpcprofiles)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `allowUnknownFields` _boolean_ |  |  |  |
| `maximumDataLength` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |


#### APPolicyGrpcProfiles





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `associateUrls` _boolean_ |  |  |  |
| `attackSignaturesCheck` _boolean_ |  |  |  |
| `decodeStringValuesAsBase64` _string_ |  |  |  |
| `defenseAttributes` _[APPolicyGrpcDefenseAttributes](#appolicygrpcdefenseattributes)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `description` _string_ |  |  |  |
| `hasIdlFiles` _boolean_ |  |  |  |
| `idlFiles` _[APPolicyIdlFilesProfiles](#appolicyidlfilesprofiles) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `metacharCheck` _boolean_ |  |  |  |
| `metacharElementCheck` _boolean_ |  |  |  |
| `name` _string_ |  |  |  |
| `signatureOverrides` _[APPolicySignatureOverrides](#appolicysignatureoverrides) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |


#### APPolicyHeaderSettings





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `maximumHttpHeaderLength` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |


#### APPolicyHeaders





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `allowRepeatedOccurrences` _boolean_ |  |  |  |
| `signatureOverrides` _[APPolicySignatureOverrides](#appolicysignatureoverrides) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `base64Decoding` _boolean_ |  |  |  |
| `maskValueInLogs` _boolean_ |  |  |  |
| `htmlNormalization` _boolean_ |  |  |  |
| `urlNormalization` _boolean_ |  |  |  |
| `name` _string_ |  |  |  |
| `normalizationViolations` _boolean_ |  |  |  |
| `type` _string_ |  |  |  |
| `mandatory` _boolean_ |  |  |  |
| `percentDecoding` _boolean_ |  |  |  |
| `checkSignatures` _boolean_ |  |  |  |
| `decodeValueAsBase64` _string_ |  |  |  |
| `wildcardOrder` _integer_ |  |  |  |


#### APPolicyHostNames





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `name` _string_ |  |  |  |
| `includeSubdomains` _boolean_ |  |  |  |


#### APPolicyHtml5CrossOriginRequestsEnforcement





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyUrls](#appolicyurls)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `allowOriginsEnforcementMode` _string_ |  |  |  |
| `checkAllowedMethods` _boolean_ |  |  |  |
| `crossDomainAllowedOrigin` _[APPolicyCrossDomainAllowedOrigin](#appolicycrossdomainallowedorigin) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `enforcementMode` _string_ |  |  |  |


#### APPolicyHttpprotocols





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyBlockingSettings](#appolicyblockingsettings)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `description` _string_ |  |  |  |
| `enabled` _boolean_ |  |  |  |
| `maxCookies` _integer_ |  |  | Maximum: 100 <br />Minimum: 1 <br /> |
| `maxHeaders` _integer_ |  |  | Maximum: 150 <br />Minimum: 1 <br /> |
| `maxParams` _integer_ |  |  | Maximum: 5000 <br />Minimum: 1 <br /> |


#### APPolicyIdlFiles





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyIdlFilesProfiles](#appolicyidlfilesprofiles)
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `contents` _string_ |  |  |  |
| `isBase64` _boolean_ |  |  |  |
| `fileName` _string_ |  |  |  |


#### APPolicyIdlFilesProfiles





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyGrpcProfiles](#appolicygrpcprofiles)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `idlFile` _[APPolicyIdlFiles](#appolicyidlfiles)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `importUrl` _string_ |  |  |  |
| `isPrimary` _boolean_ |  |  |  |
| `primaryIdlFileName` _string_ |  |  |  |


#### APPolicyJsonDefenseAttributes





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyJsonProfiles](#appolicyjsonprofiles)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `maximumTotalLengthOfJSONData` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `maximumArrayLength` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `maximumStructureDepth` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `maximumValueLength` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `tolerateJSONParsingWarnings` _boolean_ |  |  |  |


#### APPolicyJsonProfiles





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `defenseAttributes` _[APPolicyJsonDefenseAttributes](#appolicyjsondefenseattributes)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `name` _string_ |  |  |  |
| `hasValidationFiles` _boolean_ |  |  |  |
| `handleJsonValuesAsParameters` _boolean_ |  |  |  |
| `description` _string_ |  |  |  |
| `metacharOverrides` _[APPolicyCharacterSet](#appolicycharacterset) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `signatureOverrides` _[APPolicySignatureOverrides](#appolicysignatureoverrides) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `validationFiles` _[APPolicyValidationFile](#appolicyvalidationfile) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `attackSignaturesCheck` _boolean_ |  |  |  |


#### APPolicyList



APPolicyList contains a list of APPolicy

_Validation:_
- XPreserveUnknownFields: {}



| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `apiVersion` _string_ | `appprotect.f5.com/v1` | | |
| `kind` _string_ | `APPolicyList` | | |
| `metadata` _[ListMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#listmeta-v1-meta)_ | Refer to Kubernetes API documentation for fields of `metadata`. |  |  |
| `items` _[APPolicy](#appolicy) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |


#### APPolicyMethodOverrides





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyUrls](#appolicyurls)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `allowed` _boolean_ |  |  |  |
| `method` _string_ |  |  |  |


#### APPolicyMethods





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `name` _string_ |  |  |  |


#### APPolicyMitigationSignatures





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyMitigations](#appolicymitigations)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `action` _string_ |  |  |  |
| `name` _string_ |  |  |  |


#### APPolicyMitigations





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyBotDefense](#appolicybotdefense)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `anomalies` _[APPolicyAnomalies](#appolicyanomalies) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `browsers` _[APPolicyBrowsers](#appolicybrowsers) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `classes` _[APPolicyClasses](#appolicyclasses) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `signatures` _[APPolicyMitigationSignatures](#appolicymitigationsignatures) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |


#### APPolicyModifications





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicySpec](#appolicyspec)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `action` _string_ |  |  |  |
| `description` _string_ |  |  |  |
| `entity` _[APPolicyEntity](#appolicyentity)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `entityChanges` _[APPolicyEntityChanges](#appolicyentitychanges)_ |  |  | XPreserveUnknownFields: \{\} <br /> |


#### APPolicyParameters





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)
- [APPolicyPositionalParameters](#appolicypositionalparameters)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `maximumValue` _integer_ |  |  |  |
| `minimumValue` _integer_ |  |  |  |
| `multipleOf` _integer_ |  |  |  |
| `isBase64` _boolean_ |  |  |  |
| `mandatory` _boolean_ |  |  |  |
| `allowEmptyValue` _boolean_ |  |  |  |
| `allowRepeatedParameterName` _boolean_ |  |  |  |
| `attackSignaturesCheck` _boolean_ |  |  |  |
| `checkMaxValueLength` _boolean_ |  |  |  |
| `checkMetachars` _boolean_ |  |  |  |
| `level` _string_ |  |  |  |
| `metacharsOnParameterValueCheck` _boolean_ |  |  |  |
| `name` _string_ |  |  |  |
| `sensitiveParameter` _boolean_ |  |  |  |
| `type` _string_ |  |  |  |
| `nameMetacharOverrides` _[APPolicyCharacterSet](#appolicycharacterset) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `signatureOverrides` _[APPolicySignatureOverrides](#appolicysignatureoverrides) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `valueMetacharOverrides` _[APPolicyCharacterSet](#appolicycharacterset) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `arraySerializationFormat` _string_ |  |  |  |
| `checkMaxValue` _boolean_ |  |  |  |
| `checkMinValue` _boolean_ |  |  |  |
| `checkMinValueLength` _boolean_ |  |  |  |
| `checkMultipleOfValue` _boolean_ |  |  |  |
| `dataType` _string_ |  |  |  |
| `disallowFileUploadOfExecutables` _boolean_ |  |  |  |
| `enableRegularExpression` _boolean_ |  |  |  |
| `exclusiveMax` _boolean_ |  |  |  |
| `exclusiveMin` _boolean_ |  |  |  |
| `isCookie` _boolean_ |  |  |  |
| `isHeader` _boolean_ |  |  |  |
| `minimumLength` _integer_ |  |  |  |
| `maximumLength` _integer_ |  |  |  |
| `objectSerializationStyle` _string_ |  |  |  |
| `parameterEnumValues` _string array_ |  |  |  |
| `parameterLocation` _string_ |  |  |  |
| `regularExpression` _string_ |  |  |  |
| `staticValues` _string_ |  |  |  |
| `valueType` _string_ |  |  |  |
| `contentProfile` _[APPolicyContentProfile](#appolicycontentprofile)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `decodeValueAsBase64` _string_ |  |  |  |
| `wildcardOrder` _integer_ |  |  |  |
| `url` _[APPolicyUrl](#appolicyurl)_ |  |  | XPreserveUnknownFields: \{\} <br /> |


#### APPolicyPolicy





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicySpec](#appolicyspec)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$ref` _string_ | Reference to external JSON policy file |  | Optional: \{\} <br /> |
| `externalReferenceDetails` _[APPolicyExternalReferenceDetails](#appolicyexternalreferencedetails)_ | External reference details for policies fetched from Git repositories<br />Required when $ref points to a Git repository |  | XPreserveUnknownFields: \{\} <br />Optional: \{\} <br /> |
| `name` _string_ |  |  |  |
| `template` _[APPolicyTemplate](#appolicytemplate)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `applicationLanguage` _string_ |  |  |  |
| `enforcementMode` _string_ |  |  |  |
| `blocking-settings` _[APPolicyBlockingSettings](#appolicyblockingsettings)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `signature-settings` _[APPolicySignatureSettings](#appolicysignaturesettings)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `server-technologies` _[APPolicyServerTechnologies](#appolicyservertechnologies) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `headers` _[APPolicyHeaders](#appolicyheaders) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `host-names` _[APPolicyHostNames](#appolicyhostnames) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `cookies` _[APPolicyCookies](#appolicycookies) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `data-guard` _[APPolicyDataGuard](#appolicydataguard)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `filetypes` _[APPolicyFiletypes](#appolicyfiletypes) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `graphql-profiles` _[APPolicyGraphqlProfiles](#appolicygraphqlprofiles) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `enforcer-settings` _[APPolicyEnforcerSettings](#appolicyenforcersettings)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `methods` _[APPolicyMethods](#appolicymethods) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `general` _[APPolicyGeneral](#appolicygeneral)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `parameters` _[APPolicyParameters](#appolicyparameters) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `sensitive-parameters` _[APPolicySensitiveParameters](#appolicysensitiveparameters) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `json-profiles` _[APPolicyJsonProfiles](#appolicyjsonprofiles) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `xml-profiles` _[APPolicyXmlProfiles](#appolicyxmlprofiles) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `whitelist-ips` _[APPolicyWhitelistIps](#appolicywhitelistips) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `response-pages` _[APPolicyResponsePages](#appolicyresponsepages) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `browser-definitions` _[APPolicyBrowserDefinitions](#appolicybrowserdefinitions) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `caseInsensitive` _boolean_ |  |  |  |
| `character-sets` _[APPolicyCharacterSets](#appolicycharactersets) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `cookie-settings` _[APPolicyCookieSettings](#appolicycookiesettings)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `disallowed-geolocations` _[DisallowedGeolocations](#disallowedgeolocations) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `disallowedGeolocationReference` _[APPolicyDisallowedGeolocationReference](#appolicydisallowedgeolocationreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `enablePassiveMode` _boolean_ |  |  |  |
| `fullPath` _string_ |  |  |  |
| `header-settings` _[APPolicyHeaderSettings](#appolicyheadersettings)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `json-validation-files` _[APPolicyValidationFiles](#appolicyvalidationfiles) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `xml-validation-files` _[APPolicyValidationFiles](#appolicyvalidationfiles) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `signature-sets` _[APPolicySignatureSets](#appolicysignaturesets) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `signatures` _[APPolicySignatureOverrides](#appolicysignatureoverrides) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `softwareVersion` _string_ |  |  |  |
| `urls` _[APPolicyUrls](#appolicyurls) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `description` _string_ |  |  |  |
| `open-api-files` _[APPolicyReference](#appolicyreference) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `signature-requirements` _[APPolicySignatureRequirements](#appolicysignaturerequirements) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `threat-campaigns` _[APPolicyThreatCampaigns](#appolicythreatcampaigns) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `bot-defense` _[APPolicyBotDefense](#appolicybotdefense)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `idl-files` _[APPolicyIdlFiles](#appolicyidlfiles) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `grpc-profiles` _[APPolicyGrpcProfiles](#appolicygrpcprofiles) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `csrf-urls` _[APPolicyCsrfUrls](#appolicycsrfurls) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `csrf-protection` _[APPolicyCsrfProtection](#appolicycsrfprotection)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `blockingSettingReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `signatureSettingReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `serverTechnologyReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `headerReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `cookieReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `dataGuardReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `filetypeReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `methodReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `generalReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `parameterReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `sensitiveParameterReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `jsonProfileReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `xmlProfileReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `whitelistIpReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `responsePageReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `characterSetReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `cookieSettingsReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `headerSettingsReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `jsonValidationFileReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `xmlValidationFileReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `signatureSetReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `signatureReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `urlReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `threatCampaignReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |


#### APPolicyPositionalParameters





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyUrls](#appolicyurls)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `urlSegmentIndex` _integer_ |  |  |  |
| `parameter` _[APPolicyParameters](#appolicyparameters)_ |  |  | XPreserveUnknownFields: \{\} <br /> |


#### APPolicyReference





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)
- [APPolicySpec](#appolicyspec)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `link` _string_ |  |  | Pattern: `^http` <br /> |


#### APPolicyRepositoryDetails



APPolicyRepositoryDetails defines Git repository configuration

_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyExternalReferenceDetails](#appolicyexternalreferencedetails)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `repository` _string_ | Git repository URL (required) |  | MinLength: 1 <br />Required: \{\} <br /> |
| `ref` _string_ | Git reference: branch, tag, or commit SHA (required). |  | MinLength: 1 <br />Required: \{\} <br /> |


#### APPolicyResponseCode

_Underlying type:_ _integer_



_Validation:_
- Maximum: 999
- Minimum: 100

_Appears in:_
- [APPolicyGeneral](#appolicygeneral)



#### APPolicyResponseEnforcement





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyGraphqlProfiles](#appolicygraphqlprofiles)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `blockDisallowedPatterns` _boolean_ |  |  |  |
| `disallowedPatterns` _string array_ |  |  |  |


#### APPolicyResponsePages





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `responseContent` _string_ |  |  |  |
| `responseHeader` _string_ |  |  |  |
| `responseActionType` _string_ |  |  |  |
| `responsePageType` _string_ |  |  |  |
| `ajaxActionType` _string_ |  |  |  |
| `ajaxCustomContent` _string_ |  |  |  |
| `ajaxEnabled` _boolean_ |  |  |  |
| `ajaxPopupMessage` _string_ |  |  |  |
| `ajaxRedirectUrl` _string_ |  |  |  |
| `responseRedirectUrl` _string_ |  |  |  |
| `grpcStatusCode` _string_ |  |  |  |
| `grpcStatusMessage` _string_ |  |  |  |


#### APPolicySensitiveData





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyGraphqlProfiles](#appolicygraphqlprofiles)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `parameterName` _string_ |  |  |  |


#### APPolicySensitiveParameters





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `name` _string_ |  |  |  |


#### APPolicyServerTechnologies





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `serverTechnologyName` _string_ |  |  |  |


#### APPolicySettings





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyBotDefense](#appolicybotdefense)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `isEnabled` _boolean_ |  |  |  |
| `caseSensitiveHttpHeaders` _boolean_ |  |  |  |


#### APPolicySignatureOverrides





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyCookies](#appolicycookies)
- [APPolicyGraphqlProfiles](#appolicygraphqlprofiles)
- [APPolicyGrpcProfiles](#appolicygrpcprofiles)
- [APPolicyHeaders](#appolicyheaders)
- [APPolicyJsonProfiles](#appolicyjsonprofiles)
- [APPolicyParameters](#appolicyparameters)
- [APPolicyPolicy](#appolicypolicy)
- [APPolicyUrls](#appolicyurls)
- [APPolicyXmlProfiles](#appolicyxmlprofiles)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `enabled` _boolean_ |  |  |  |
| `signatureId` _integer_ |  |  |  |
| `tag` _string_ |  |  |  |
| `name` _string_ |  |  |  |


#### APPolicySignatureRequirements





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `tag` _string_ |  |  |  |


#### APPolicySignatureSet





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicySignatureSets](#appolicysignaturesets)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `filter` _[APPolicySignatureSetFilter](#appolicysignaturesetfilter)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `signatures` _[APPolicySignatures](#appolicysignatures) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `systems` _[APPolicySystems](#appolicysystems) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `type` _[APPolicySignatureSetType](#appolicysignaturesettype)_ |  |  | Enum: [filter-based manual] <br /> |


#### APPolicySignatureSetFilter





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicySignatureSet](#appolicysignatureset)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `accuracyFilter` _[APPolicyFilterAccuracyFilter](#appolicyfilteraccuracyfilter)_ |  |  | Enum: [all eq ge le] <br /> |
| `accuracyValue` _[APPolicyFilterAccuracyValue](#appolicyfilteraccuracyvalue)_ |  |  | Enum: [high low medium] <br /> |
| `attackType` _[APPolicyAttackType](#appolicyattacktype)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `hasCve` _[APPolicyFilterHasCve](#appolicyfilterhascve)_ |  |  | Enum: [all false true] <br /> |
| `lastUpdatedFilter` _[APPolicyFilterLastUpdatedFilter](#appolicyfilterlastupdatedfilter)_ |  |  | Enum: [all eq ge le] <br /> |
| `lastUpdatedValue` _string_ |  |  |  |
| `riskFilter` _[APPolicyFilterRiskFilter](#appolicyfilterriskfilter)_ |  |  | Enum: [all eq ge le] <br /> |
| `riskValue` _[APPolicyFilterRiskValue](#appolicyfilterriskvalue)_ |  |  | Enum: [high low medium] <br /> |
| `signatureType` _[APPolicyFilterSignatureType](#appolicyfiltersignaturetype)_ |  |  | Enum: [all request response] <br /> |
| `tagFilter` _[APPolicyFilterTagFilter](#appolicyfiltertagfilter)_ |  |  | Enum: [all eq untagged] <br /> |
| `tagValue` _string_ |  |  |  |
| `userDefinedFilter` _[APPolicyFilterUserDefinedFilter](#appolicyfilteruserdefinedfilter)_ |  |  | Enum: [all false true] <br /> |


#### APPolicySignatureSetType

_Underlying type:_ _string_





_Appears in:_
- [APPolicySignatureSet](#appolicysignatureset)

| Field | Description |
| --- | --- |
| `filter-based` |  |
| `manual` |  |


#### APPolicySignatureSets





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `name` _string_ |  |  |  |
| `block` _boolean_ |  |  |  |
| `alarm` _boolean_ |  |  |  |
| `learn` _boolean_ |  |  |  |
| `signatureSet` _[APPolicySignatureSet](#appolicysignatureset)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `stagingCertificationDatetime` _[APPolicySignatureSetsStagingCertificationDatetime](#appolicysignaturesetsstagingcertificationdatetime)_ |  |  | Enum: [] <br /> |


#### APPolicySignatureSetsStagingCertificationDatetime

_Underlying type:_ _string_

Enum types



_Appears in:_
- [APPolicySignatureSets](#appolicysignaturesets)

| Field | Description |
| --- | --- |
| `` |  |


#### APPolicySignatureSettings





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `attackSignatureFalsePositiveMode` _string_ |  |  |  |
| `minimumAccuracyForAutoAddedSignatures` _string_ |  |  |  |


#### APPolicySignatures





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicySignatureSet](#appolicysignatureset)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `alarm` _boolean_ |  |  |  |
| `block` _boolean_ |  |  |  |
| `enabled` _boolean_ |  |  |  |
| `inPolicy` _[APPolicySignaturesInPolicy](#appolicysignaturesinpolicy)_ |  |  | Enum: [0 1] <br /> |
| `isPriorRuleEnforced` _boolean_ |  |  |  |
| `learn` _boolean_ |  |  |  |
| `name` _string_ |  |  |  |
| `performStaging` _boolean_ |  |  |  |
| `signatureId` _integer_ |  |  |  |
| `tag` _string_ |  |  |  |


#### APPolicySignaturesInPolicy

_Underlying type:_ _string_





_Appears in:_
- [APPolicySignatures](#appolicysignatures)

| Field | Description |
| --- | --- |
| `0` |  |
| `1` |  |


#### APPolicySpec



APPolicySpec defines the desired state of APPolicy



_Appears in:_
- [APPolicy](#appolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `policy` _[APPolicyPolicy](#appolicypolicy)_ | Defines the App Protect policy - can be inline policy or reference |  | XPreserveUnknownFields: \{\} <br /> |
| `modifications` _[APPolicyModifications](#appolicymodifications) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `modificationsReference` _[APPolicyReference](#appolicyreference)_ |  |  | XPreserveUnknownFields: \{\} <br /> |


#### APPolicyStatus



APPolicyStatus defines the observed state of Policy

_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicy](#appolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `bundle` _[APPolicyBundleStatus](#appolicybundlestatus)_ | Bundle holds the “ready/pending/invalid” bundle info |  | XPreserveUnknownFields: \{\} <br />Optional: \{\} <br /> |
| `processing` _[ProcessingStatus](#processingstatus)_ | Processing holds the compiler/validation metadata |  | Optional: \{\} <br /> |
| `observedPolicyName` _string_ | ObservedPolicyName is the policy name as declared inside the policy<br />file/bundle itself. This is usually identical to the APPolicy CR name,<br />but it is not guaranteed, especially when the policy is fetched from<br />external references. |  | Optional: \{\} <br /> |
| `observedGeneration` _integer_ | ObservedGeneration is the most recent metadata.generation for which the<br />controller successfully reconciled (compiled) the policy bundle.<br />This field tracks the Kubernetes metadata.generation to determine if<br />a new compilation is needed when the spec changes.<br />If metadata.generation is greater than this value, the controller will<br />trigger a new compilation. |  | Optional: \{\} <br /> |
| `inProgressGeneration` _integer_ | InProgressGeneration records the metadata.generation for which a<br />compilation job is currently pending or processing.<br />This allows the controller to avoid mis-attributing compilation results<br />when the spec changes mid-flight. |  | Optional: \{\} <br /> |
| `lastAppliedRevision` _string_ | LastAppliedRevision records the revision from metadata.annotations<br />that was used for the last successful compilation. If the current<br />metadata revision differs from this value, the controller will<br />trigger a recompilation. |  | Optional: \{\} <br /> |
| `currentRevisionInProgress` _string_ | CurrentRevisionInProgress records the revision from metadata.annotations<br />for which a compilation job is currently pending or processing. This<br />allows the controller to avoid starting duplicate jobs for the same<br />revision, while still permitting a new job when the desired revision<br />changes mid-flight. |  | Optional: \{\} <br /> |
| `lastGoodBundle` _[APPolicyBundleStatus](#appolicybundlestatus)_ | LastGoodBundle stores the most recent successfully compiled bundle metadata.<br />This field is only populated when the current bundle state is NOT "ready",<br />to enable fallback to the last known good configuration. |  | XPreserveUnknownFields: \{\} <br />Optional: \{\} <br /> |
| `previousBundleLocation` _string_ | PreviousBundleLocation stores the S3 location of the previous (N-1) bundle.<br />When a new bundle is compiled, the old bundle is NOT deleted immediately<br />because traffic nodes may still be fetching it. Instead, the old location<br />is saved here. On the NEXT successful compilation, the bundle at this<br />location (now N-2) is deleted, and the current bundle location takes its place. |  | Optional: \{\} <br /> |


#### APPolicySystems





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicySignatureSet](#appolicysignatureset)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `name` _string_ |  |  |  |


#### APPolicyTemplate





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `name` _string_ |  |  |  |


#### APPolicyThreatCampaigns





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `isEnabled` _boolean_ |  |  |  |
| `name` _string_ |  |  |  |


#### APPolicyUrl





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyParameters](#appolicyparameters)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `method` _string_ |  |  |  |
| `name` _string_ |  |  |  |
| `protocol` _string_ |  |  |  |
| `type` _string_ |  |  |  |


#### APPolicyUrlContentProfiles





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyUrls](#appolicyurls)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `name` _string_ |  |  |  |
| `contentProfile` _[APPolicyContentProfile](#appolicycontentprofile)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `headerName` _string_ |  |  |  |
| `headerOrder` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `headerValue` _string_ |  |  |  |
| `type` _string_ |  |  |  |


#### APPolicyUrls





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `method` _string_ |  |  |  |
| `name` _string_ |  |  |  |
| `protocol` _string_ |  |  |  |
| `description` _string_ |  |  |  |
| `metacharOverrides` _[APPolicyCharacterSet](#appolicycharacterset) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `metacharsOnUrlCheck` _boolean_ |  |  |  |
| `attackSignaturesCheck` _boolean_ |  |  |  |
| `disallowFileUploadOfExecutables` _boolean_ |  |  |  |
| `html5CrossOriginRequestsEnforcement` _[APPolicyHtml5CrossOriginRequestsEnforcement](#appolicyhtml5crossoriginrequestsenforcement)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `isAllowed` _boolean_ |  |  |  |
| `mandatoryBody` _boolean_ |  |  |  |
| `methodOverrides` _[APPolicyMethodOverrides](#appolicymethodoverrides) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `methodsOverrideOnUrlCheck` _boolean_ |  |  |  |
| `operationId` _string_ |  |  |  |
| `positionalParameters` _[APPolicyPositionalParameters](#appolicypositionalparameters) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `signatureOverrides` _[APPolicySignatureOverrides](#appolicysignatureoverrides) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `type` _string_ |  |  |  |
| `urlContentProfiles` _[APPolicyUrlContentProfiles](#appolicyurlcontentprofiles) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `wildcardOrder` _integer_ |  |  |  |
| `allowRenderingInFrames` _string_ |  |  |  |
| `allowRenderingInFramesOnlyFrom` _string_ |  |  |  |
| `clickjackingProtection` _boolean_ |  |  |  |


#### APPolicyValidationFile





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyJsonProfiles](#appolicyjsonprofiles)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `importUrl` _string_ |  |  |  |
| `isPrimary` _boolean_ |  |  |  |
| `jsonValidationFile` _[APPolicyValidationFiles](#appolicyvalidationfiles)_ |  |  | XPreserveUnknownFields: \{\} <br /> |


#### APPolicyValidationFiles





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)
- [APPolicyValidationFile](#appolicyvalidationfile)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `contents` _string_ |  |  |  |
| `fileName` _string_ |  |  |  |
| `isBase64` _boolean_ |  |  |  |


#### APPolicyViolations





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyBlockingSettings](#appolicyblockingsettings)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `description` _string_ |  |  |  |
| `name` _string_ |  |  |  |
| `alarm` _boolean_ |  |  |  |
| `block` _boolean_ |  |  |  |


#### APPolicyWhitelistIps





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `blockRequests` _string_ |  |  |  |
| `ipAddress` _string_ |  |  |  |
| `ipMask` _string_ |  |  |  |
| `neverLogRequests` _boolean_ |  |  |  |


#### APPolicyXmlDefenseAttributes





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyXmlProfiles](#appolicyxmlprofiles)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `maximumAttributesPerElement` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `allowCDATA` _boolean_ |  |  |  |
| `maximumDocumentDepth` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `maximumAttributeValueLength` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `maximumChildrenPerElement` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `maximumDocumentSize` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `tolerateNumericNames` _boolean_ |  |  |  |
| `maximumElements` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `tolerateLeadingWhiteSpace` _boolean_ |  |  |  |
| `tolerateCloseTagShorthand` _boolean_ |  |  |  |
| `allowDTDs` _boolean_ |  |  |  |
| `maximumNameLength` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `allowExternalReferences` _boolean_ |  |  |  |
| `maximumNSDeclarations` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `maximumNamespaceLength` _[IntOrString](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#intorstring-intstr-util)_ |  |  |  |
| `allowProcessingInstructions` _boolean_ |  |  |  |


#### APPolicyXmlProfiles





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `name` _string_ |  |  |  |
| `description` _string_ |  |  |  |
| `defenseAttributes` _[APPolicyXmlDefenseAttributes](#appolicyxmldefenseattributes)_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `attackSignaturesCheck` _boolean_ |  |  |  |
| `enableWss` _boolean_ |  |  |  |
| `followSchemaLinks` _boolean_ |  |  |  |
| `signatureOverrides` _[APPolicySignatureOverrides](#appolicysignatureoverrides) array_ |  |  | XPreserveUnknownFields: \{\} <br /> |
| `useXmlResponsePage` _boolean_ |  |  |  |


#### APSignatures



APSignatures is the Schema for the APSignatures API



_Appears in:_
- [APSignaturesList](#apsignatureslist)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `apiVersion` _string_ | `appprotect.f5.com/v1` | | |
| `kind` _string_ | `APSignatures` | | |
| `metadata` _[ObjectMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#objectmeta-v1-meta)_ | Refer to Kubernetes API documentation for fields of `metadata`. |  |  |
| `spec` _[APSignaturesSpec](#apsignaturesspec)_ |  |  |  |
| `status` _[APSignaturesStatus](#apsignaturesstatus)_ |  |  |  |


#### APSignaturesList



APSignaturesList contains a list of APSignatures





| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `apiVersion` _string_ | `appprotect.f5.com/v1` | | |
| `kind` _string_ | `APSignaturesList` | | |
| `metadata` _[ListMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#listmeta-v1-meta)_ | Refer to Kubernetes API documentation for fields of `metadata`. |  |  |
| `items` _[APSignatures](#apsignatures) array_ |  |  |  |


#### APSignaturesSpec







_Appears in:_
- [APSignatures](#apsignatures)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `attack-signatures` _[SignatureSettings](#signaturesettings)_ |  |  |  |
| `bot-signatures` _[SignatureSettings](#signaturesettings)_ |  |  |  |
| `threat-campaigns` _[SignatureSettings](#signaturesettings)_ |  |  |  |
| `repository` _[SignatureRepository](#signaturerepository)_ | Repository defines optional configuration for a custom signature repository.<br />If set, APSignatures will download from the provided repository instead of pkgs.nginx.com. |  | Optional: \{\} <br /> |


#### APSignaturesStatus







_Appears in:_
- [APSignatures](#apsignatures)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `attack-signatures` _[SecurityUpdateStatus](#securityupdatestatus)_ |  |  |  |
| `bot-signatures` _[SecurityUpdateStatus](#securityupdatestatus)_ |  |  |  |
| `threat-campaigns` _[SecurityUpdateStatus](#securityupdatestatus)_ |  |  |  |
| `installationState` _[InstallationState](#installationstate)_ | InstallationState is the current installation state (installing, success, failure) |  | Enum: [installing success failure] <br /> |
| `observedGeneration` _integer_ | ObservedGeneration records the .metadata.generation that was last fully processed.<br />Used to distinguish user-initiated reconciles (spec change) from periodic requeues. |  | Optional: \{\} <br /> |
| `errors` _string_ |  |  | Optional: \{\} <br /> |


#### APUserSig



APUserSig is the Schema for the apusersigs API



_Appears in:_
- [APUserSigList](#apusersiglist)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `apiVersion` _string_ | `appprotect.f5.com/v1` | | |
| `kind` _string_ | `APUserSig` | | |
| `metadata` _[ObjectMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#objectmeta-v1-meta)_ | Refer to Kubernetes API documentation for fields of `metadata`. |  |  |
| `spec` _[APUserSigSpec](#apusersigspec)_ |  |  |  |
| `status` _[APUserSigStatus](#apusersigstatus)_ |  |  |  |


#### APUserSigList



APUserSigList contains a list of APUserSig





| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `apiVersion` _string_ | `appprotect.f5.com/v1` | | |
| `kind` _string_ | `APUserSigList` | | |
| `metadata` _[ListMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#listmeta-v1-meta)_ | Refer to Kubernetes API documentation for fields of `metadata`. |  |  |
| `items` _[APUserSig](#apusersig) array_ |  |  |  |


#### APUserSigPolicyUpdateState

_Underlying type:_ _[PolicyUpdateState](#policyupdatestate)_

APUserSigPolicyUpdateState is the type for policy update state values after changes in User Defined Signatures

_Validation:_
- Enum: [complete ongoing]

_Appears in:_
- [APUserSigStatus](#apusersigstatus)



#### APUserSigSpec



APUserSigSpec defines the desired state of APUserSig



_Appears in:_
- [APUserSig](#apusersig)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `properties` _string_ |  |  |  |
| `signatures` _[UserSignature](#usersignature) array_ |  |  |  |
| `softwareVersion` _string_ |  |  |  |
| `tag` _string_ |  |  |  |


#### APUserSigStatus



APUsersigStatus defines the observed state of Usersig



_Appears in:_
- [APUserSig](#apusersig)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `installationState` _[InstallationState](#installationstate)_ | InstallationState represents the installation status: success, installing, or failure |  | Enum: [success installing failure] <br /> |
| `policyUpdateState` _[APUserSigPolicyUpdateState](#apusersigpolicyupdatestate)_ | PolicyUpdateState represents the state of embedding new signature updates in policies: complete or ongoing |  | Enum: [complete ongoing] <br /> |
| `processing` _[ProcessingStatus](#processingstatus)_ | Processing holds upload/validation metadata. |  | Optional: \{\} <br /> |
| `observedGeneration` _integer_ | ObservedGeneration is the most recent metadata.generation for which the<br />controller successfully processed this APUserSig resource.<br />This field tracks the Kubernetes metadata.generation to determine if<br />the resource needs reprocessing when the spec changes. |  | Optional: \{\} <br /> |


#### AttackType







_Appears in:_
- [UserSignature](#usersignature)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `name` _string_ |  |  |  |


#### BundleSignatures



BundleSignatures holds timestamps of the individual signature sets

_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyBundleStatus](#appolicybundlestatus)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `attackSignatures` _[Time](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#time-v1-meta)_ | AttackSignatures is the timestamp of the attack signatures |  | Optional: \{\} <br /> |
| `botSignatures` _[Time](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#time-v1-meta)_ | BotSignatures is the timestamp of the bot signatures |  | Optional: \{\} <br /> |
| `threatCampaigns` _[Time](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#time-v1-meta)_ | ThreatCampaigns is the timestamp of the threat campaigns signatures |  | Optional: \{\} <br /> |


#### BundleState

_Underlying type:_ _string_

BundleState is an enum for the bundle state



_Appears in:_
- [APPolicyBundleStatus](#appolicybundlestatus)
- [BundleStatus](#bundlestatus)

| Field | Description |
| --- | --- |
| `pending` |  |
| `processing` |  |
| `ready` |  |
| `invalid` |  |


#### BundleStatus



BundleStatus reports on the actual bundle tar-ball and its state



_Appears in:_
- [APLogConfStatus](#aplogconfstatus)
- [APPolicyBundleStatus](#appolicybundlestatus)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `state` _[BundleState](#bundlestate)_ | State is the current bundle state (pending, processing, ready, invalid) |  | Enum: [pending processing ready invalid] <br /> |
| `location` _string_ | Location is the path/URL where the compiled bundle is stored; only set when State == “ready” |  | Optional: \{\} <br /> |
| `sha256` _string_ | Sha256 is the SHA256 hash of the bundle file |  | Optional: \{\} <br /> |
| `compilerVersion` _string_ | CompilerVersion is the version of the compiler used to build this bundle. |  | Optional: \{\} <br /> |


#### DisallowedGeolocations





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [APPolicyPolicy](#appolicypolicy)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `$action` _string_ |  |  |  |
| `countryCode` _string_ |  |  |  |
| `countryName` _string_ |  |  |  |


#### EscapingCharacter







_Appears in:_
- [LogConfContent](#logconfcontent)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `from` _string_ |  |  |  |
| `to` _string_ |  |  |  |


#### InstallationState

_Underlying type:_ _string_

InstallationState is an enum for the installation state



_Appears in:_
- [APSignaturesStatus](#apsignaturesstatus)
- [APUserSigStatus](#apusersigstatus)

| Field | Description |
| --- | --- |
| `installing` |  |
| `success` |  |
| `failure` |  |


#### LogConfContent







_Appears in:_
- [APLogConfSpec](#aplogconfspec)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `escaping_characters` _[EscapingCharacter](#escapingcharacter) array_ |  |  |  |
| `format` _string_ |  |  | Enum: [splunk arcsight default user-defined grpc] <br /> |
| `format_string` _string_ |  |  |  |
| `list_delimiter` _string_ |  |  |  |
| `list_prefix` _string_ |  |  |  |
| `list_suffix` _string_ |  |  |  |
| `max_message_size` _string_ |  |  | Pattern: `^([1-9]\|[1-5][0-9]\|6[0-4])k$` <br /> |
| `max_request_size` _string_ |  |  | Pattern: `^([1-9]\|[1-9][0-9]\|[1-9][0-9]\{2\}\|[1-9][0-9]\{3\}\|10[0-2][0-9][0-9]\|[1-9]k\|10k\|any)$` <br /> |


#### LogConfFilter







_Appears in:_
- [APLogConfSpec](#aplogconfspec)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `request_type` _string_ |  |  | Enum: [all illegal blocked] <br /> |


#### PolicyUpdateState

_Underlying type:_ _string_





_Appears in:_
- [APUserSigPolicyUpdateState](#apusersigpolicyupdatestate)

| Field | Description |
| --- | --- |
| `complete` |  |
| `ongoing` |  |
| `modified-only` |  |


#### ProcessingStatus



ProcessingStatus holds compile/validation info



_Appears in:_
- [APLogConfStatus](#aplogconfstatus)
- [APPolicyStatus](#appolicystatus)
- [APUserSigStatus](#apusersigstatus)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `isCompiled` _boolean_ | IsCompiled is true if we compiled the bundle; false means we accepted a pre-compiled one. |  | Optional: \{\} <br /> |
| `datetime` _[Time](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.29/#time-v1-meta)_ | Datetime is when the last compile/validation occurred. |  | Optional: \{\} <br /> |
| `errors` _string array_ | Errors holds any validation or compile errors (only if State == “invalid”) |  | Optional: \{\} <br /> |


#### Reference







_Appears in:_
- [UserSignature](#usersignature)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `type` _string_ |  |  | Enum: [bugtraq cve nessus url] <br /> |
| `value` _string_ |  |  |  |


#### SecretReference



SecretReference is a reference to a Kubernetes secret by name.



_Appears in:_
- [SignatureRepositoryTLS](#signaturerepositorytls)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `secretName` _string_ | SecretName is the name of the Kubernetes secret. |  |  |


#### SecurityUpdateStatus







_Appears in:_
- [APSignaturesStatus](#apsignaturesstatus)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `isInstalledRevisionLatest` _boolean_ |  |  |  |
| `installedRevision` _string_ |  |  |  |
| `latestAvailableRevision` _string_ |  |  |  |


#### SignatureRepository







_Appears in:_
- [APSignaturesSpec](#apsignaturesspec)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `baseUrl` _string_ | BaseUrl is the base URL where signature .deb packages are hosted. |  |  |
| `authentication` _[SignatureRepositoryAuth](#signaturerepositoryauth)_ | Authentication configures optional credentials for the repository. |  | Optional: \{\} <br /> |
| `tls` _[SignatureRepositoryTLS](#signaturerepositorytls)_ | TLS configures optional TLS settings for the repository. |  | Optional: \{\} <br /> |


#### SignatureRepositoryAuth







_Appears in:_
- [SignatureRepository](#signaturerepository)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `type` _[SignatureRepositoryAuthType](#signaturerepositoryauthtype)_ | Type indicates the authentication type (bearer or basic). Required when authentication is configured. |  | Enum: [bearer basic] <br /> |
| `secretName` _string_ | SecretName is the name of a Kubernetes secret containing the credentials.<br />For bearer: the secret must have a "token" key.<br />For basic: the secret must have "username" and "password" keys. |  |  |


#### SignatureRepositoryAuthType

_Underlying type:_ _string_





_Appears in:_
- [SignatureRepositoryAuth](#signaturerepositoryauth)

| Field | Description |
| --- | --- |
| `bearer` |  |
| `basic` |  |


#### SignatureRepositoryTLS







_Appears in:_
- [SignatureRepository](#signaturerepository)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `clientCertificate` _[SecretReference](#secretreference)_ | ClientCertificate references a secret that contains a client TLS certificate and key.<br />Expected keys: tls.crt and tls.key (security-updates-repo.crt/key are also accepted for compatibility). |  | Optional: \{\} <br /> |
| `caBundle` _[SecretReference](#secretreference)_ | CABundle references a secret containing a PEM-encoded CA bundle (key: ca.crt). |  | Optional: \{\} <br /> |
| `verifyCertificate` _boolean_ | VerifyCertificate controls whether the server's TLS certificate is verified.<br />Defaults to true. Set to false to skip verification (use with caution, for dev/test only). | true | Optional: \{\} <br /> |


#### SignatureSettings







_Appears in:_
- [APSignaturesSpec](#apsignaturesspec)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `revision` _string_ | Revision is the desired signature revision (e.g. "2026.01.01-3" or "latest"). |  |  |




#### SomeType





_Validation:_
- XPreserveUnknownFields: {}

_Appears in:_
- [SomeStructure](#somestructure)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `type` _string_ |  |  |  |


#### System







_Appears in:_
- [UserSignature](#usersignature)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `name` _string_ |  |  |  |


#### UserSignature







_Appears in:_
- [APUserSigSpec](#apusersigspec)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `accuracy` _string_ |  |  | Enum: [high medium low] <br /> |
| `attackType` _[AttackType](#attacktype)_ |  |  |  |
| `description` _string_ |  |  |  |
| `name` _string_ |  |  |  |
| `references` _[Reference](#reference)_ |  |  |  |
| `risk` _string_ |  |  | Enum: [high medium low] <br /> |
| `rule` _string_ |  |  |  |
| `signatureType` _string_ |  |  | Enum: [request response] <br /> |
| `systems` _[System](#system) array_ |  |  |  |


