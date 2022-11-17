# 0000: AO Custom Fields
<!-- Leave this ID at 0000. The ECS team will assign a unique, contiguous RFC number upon merging the initial stage of this RFC. -->

- Stage: **0** <!-- Update to reflect target stage. See https://elastic.github.io/ecs/stages.html -->
- Date: **TBD** <!-- The ECS team sets this date at merge time. This is the date of the latest stage advancement. -->

<!--
As you work on your RFC, use the "Stage N" comments to guide you in what you should focus on, for the stage you're targeting.
Feel free to remove these comments as you go along.
-->

<!--
Stage 0: Provide a high level summary of the premise of these changes. Briefly describe the nature, purpose, and impact of the changes. ~2-5 sentences.
-->

This RFC provides guidance for new fields to better describe entities common in cloud platforms.

<!--
Stage 1: If the changes include field additions or modifications, please create a folder titled as the RFC number under rfcs/text/. This will be where proposed schema changes as standalone YAML files or extended example mappings and larger source documents will go as the RFC is iterated upon.
-->

<!--
Stage X: Provide a brief explanation of why the proposal is being marked as abandoned. This is useful context for anyone revisiting this proposal or considering similar changes later on.
-->

## Fields

<!--
Stage 1: Describe at a high level how this change affects fields. Include new or updated yml field definitions for all of the essential fields in this draft. While not exhaustive, the fields documented here should be comprehensive enough to deeply evaluate the technical considerations of this change. The goal here is to validate the technical details for all essential fields and to provide a basis for adding experimental field definitions to the schema. Use GitHub code blocks with yml syntax formatting, and add them to the corresponding RFC folder.
-->

This RFC calls for the introduction of several top-level fields with the following child fields:

| field | type | description |
| --- | --- | --- |
| `application.name` | keyword | Name of the application |
| `application.id` | keyword | Platform assigned ID of the application |
| `application.category` | keyword | Category of the application (e.g. `api`) |
| `application.type` | keyword | Sub-category of the application (e.g. `soap_partner`) |
| `application.version` | version | Version of the application |
| `application.domain` | keyword | Domain of the application |
| `application.path` | keyword | URI of the application |
| `application.scopes` | array | Scopes of the application |
| `authentication.category` | keyword | Category of authentication (e.g. `password`, `hardware_token`, `software_token`, etc.) |
| `authentication.method` | keyword | Method of authentication |
| `authentication.provider` | keyword | Authentication IdP (e.g. `Okta`) |
| `policy.name` | keyword | The name or title of the policy |
| `policy.id` | keyword | ID of the policy |
| `policy.category` | keyword | Category of policy (e.g. `functional`, `posture`, `security`, `access`) |
| `policy.type` | keyword | Type of policy |
| `role.name` | keyword | Name of the role |
| `role.id` | keyword | ID of the role |
| `role.scopes` | array | Scopes of the role |
| `space.name` | keyword | Name of the space |
| `space.id` | keyword | ID of the space |
| `space.category` | keyword | Category of the space (e.g. `channel`, `meeting`, etc.) |
| `setting.name` | keyword | The name of the setting |
| `setting.id` | keyword | ID of the setting |
| `setting.category` | keyword | Category of setting (e.g. `user`, `organization`, etc.) |
| `setting.type` | keyword | Type of setting (e.g. `security`) |

<!--
Stage 2: Add or update all remaining field definitions. The list should now be exhaustive. The goal here is to validate the technical details of all remaining fields and to provide a basis for releasing these field definitions as beta in the schema. Use GitHub code blocks with yml syntax formatting, and add them to the corresponding RFC folder.
-->

Additional field documentation can be found for each top-level field in its corresponding RFC folder.

- [api](text/0000/api.yaml)
- [application](text/0000/application.yaml)
- [authentication](text/0000/authentication.yaml)
- [policy](text/0000/policy.yaml)
- [role](text/0000/role.yaml)
- [space](text/0000/space.yaml)

## Usage

<!--
Stage 1: Describe at a high-level how these field changes will be used in practice. Real world examples are encouraged. The goal here is to understand how people would leverage these fields to gain insights or solve problems. ~1-3 paragraphs.
-->

For entities or concepts that are common in cloud platform events, we need additional fields to fully capture the relevant information. The goal of these proposed top-level objects is to create more precise fields when normalizing cloud-related events.

## Source data

<!--
Stage 1: Provide a high-level description of example sources of data. This does not yet need to be a concrete example of a source document, but instead can simply describe a potential source (e.g. nginx access log). This will ultimately be fleshed out to include literal source examples in a future stage. The goal here is to identify practical sources for these fields in the real world. ~1-3 sentences or unordered list.
-->

<!--
Stage 2: Included a real world example source document. Ideally this example comes from the source(s) identified in stage 1. If not, it should replace them. The goal here is to validate the utility of these field changes in the context of a real world example. Format with the source name as a ### header and the example document in a GitHub code block with json formatting, or if on the larger side, add them to the corresponding RFC folder.
-->

<!--
Stage 3: Add more real world example source documents so we have at least 2 total, but ideally 3. Format as described in stage 2.
-->

## Scope of impact

<!--
Stage 2: Identifies scope of impact of changes. Are breaking changes required? Should deprecation strategies be adopted? Will significant refactoring be involved? Break the impact down into:
 * Ingestion mechanisms (e.g. beats/logstash)
 * Usage mechanisms (e.g. Kibana applications, detections)
 * ECS project (e.g. docs, tooling)
The goal here is to research and understand the impact of these changes on users in the community and development teams across Elastic. 2-5 sentences each.
-->

Currently, we are mapping most of these fields to `labels.*` or `resource.*`. For backwards compatibility in the short term, we should keep current mappings and simply copy relevant fields to the new proposed fields in this RFC. Once all rules have been reviewed, normalization using `labels.*` or `resource.*` as it relates to these proposed fields can be deprecated.

## Concerns

<!--
Stage 1: Identify potential concerns, implementation challenges, or complexity. Spend some time on this. Play devil's advocate. Try to identify the sort of non-obvious challenges that tend to surface later. The goal here is to surface risks early, allow everyone the time to work through them, and ultimately document resolution for posterity's sake.
-->

<!--
Stage 2: Document new concerns or resolutions to previously listed concerns. It's not critical that all concerns have resolutions at this point, but it would be helpful if resolutions were taking shape for the most significant concerns.
-->

<!--
Stage 3: Document resolutions for all existing concerns. Any new concerns should be documented along with their resolution. The goal here is to eliminate risk of churn and instability by ensuring all concerns have been addressed.
-->

## People

The following are the people that consulted on the contents of this RFC.

* @justinkb88 | author
* @drewgatchell | subject matter expert
* @dtocco | subject matter expert
* @lgraslie | subject matter expert

## References

<!-- Insert any links appropriate to this RFC in this section. -->

### RFC Pull Requests

<!-- An RFC should link to the PRs for each of it stage advancements. -->

* Stage 0: https://github.com/appomni/ecs/pull/1

<!--
* Stage 1: https://github.com/elastic/ecs/pull/NNN
...
-->
