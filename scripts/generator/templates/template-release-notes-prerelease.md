# Vaadin {{platform}}

Vaadin consists of a set of web components, a Java web framework, configurable themes, tools and a set of app templates.

Visit [vaadin.com](https://vaadin.com/) to get started.

## New and Noteworthy Since Vaadin 18

Here are the highlighted new and improved features in Vaadin 19. To see the full list of bug fixes and improvements, check Included Projects and Change Log.

### Flow
#### Features
- Improved LitTemplate support
Using `LitTemplate` is recommended over deprecated `PolymerTemplate` for doing layouts with HTML and UI logic in Java. It is recommended to use TypeScript for the template and this has been updated to the examples in the [documentation](https://github.com/vaadin/flow-and-components-documentation/tree/master/documentation/polymer-templates). Starting from Vaadin 18, the initial attribute values in the template are reflected to the server side state when `@Id` mapping components. This applies to `PolymerTemplate` too. More information on the template support [in the blog](https://vaadin.com/blog/future-of-html-templates-in-vaadin).

-  Add HasHelper interface 
A new `HasHelper` interface has been added to be used for field components that have a "helper" feature (such as TextField), i.e. a slot below/above input fields for supplying additional information or content related to the field.

- Supporting undefined item count for `ComboBox` and delaying count call until dropdown is opened
Starting from V18, `ComboBox` works without defining a item count query, or it can delay the count query until the drop down is opened due to changes in `DataCommunicator`. 

#### Breaking Changes
- Template support 
Future of template support is described here: https://vaadin.com/blog/future-of-html-templates-in-vaadin
**The changes in Flow 5.0 do not require changing existing `LitTemplate` or `PolymerTemplate` based components. In case you have existing workaround placed for handling the initial attribute values for template-mapped-components, those workarounds should not be needed anymore.**
  - `PolymerTemplate` related classes are now deprecated and moved from `flow-server` to `flow-polymer-template` artifact.
  - `LitTemplate` related classes are now moved from `flow-server` to `flow-lit-template` artifact.
  - `Uses` annotation is now deprecated, because Polymer template support is deprecated.

- `AppShellRegistry` method `getTitle()` is removed 
It was broken and could not work. Instead, if needed, use `getUI().getUIInternals().getAppShellTitle()`. 

### Fusion
#### Features
- Client-side Spring Security based authentication helpers  
Add `Spring Security` based authentication helpers `login`, `logout`, and an `InvalidSessionMiddleWare` for handling session expiration. This feature makes it easier to write a single-page application (SPA) with a custom login view.

- Support TypeScript form binding with optional fields and objects 
When binding to an optional object field, the TypeScript form binder will not initialize the field with an empty value and leave it as `undefined` unless there are bindings to the nested fields. This feature is necessary when e.g., binding an object field to a Combobox.

- Simpler CSS import for TypeScript views and CSS `@import` support 
This feature gives us a nice DX of importing styles to TS views like:
```ts
import styles from './list-view.css';

@customElement('list-view')
export class ListView extends LitElement {
  static styles = [Lumo, styles];
```
#### Breaking Changes

- Optional type for value property of BinderNode 
The `value` property of `BinderNode` now has optionally `undefined` type for non-initialised optional fields.

  
### Components

#### Features
- Field helpers
  - Slot below/above input fields for supplying additional information or content related to the field. 
- AutoOpenDisabled
  - mode for ComboBox, DatePicker, TimePicker, DateTimePicker that prevents dropdown from opening automatically on focus
- new component: vaadin-avatar 
  - Avatar and AvatarGroup components. Being able to show users with name, abbreviations and image. AvatarGroup is a collection of Avatars with the possibility to truncate it to a certain number of visible avatars.

#### Breaking Changes
- Flow components versioning has changed, now all components are released at once with Vaadin Platform sharing the same version.


{{changesSincePrevious}}

## Support
Vaadin 19 is supported for one month after Vaadin 20 has been released. The latest LTS (long term support) version is Vaadin 14. More details of our release model are available on our [roadmap page](https://vaadin.com/roadmap).

Vaadin also provides [commercial support and warranty](https://vaadin.com/support).

## Included Projects and Change Log
Vaadin includes the following projects. Release notes with detailed change logs for each project are linked below.

Projects marked as **(Pro)** are available for users with [Pro](https://vaadin.com/pricing) or [Prime](https://vaadin.com/pricing) subscriptions. Everything else is free and open source.

### Java Web Framework
- Vaadin Flow ([{{core.flow.javaVersion}}](https://github.com/vaadin/flow/releases/tag/{{core.flow.javaVersion}}))
- Vaadin Spring Addon ([{{core.flow-spring.javaVersion}}](https://github.com/vaadin/spring/releases/tag/{{core.flow-spring.javaVersion}}))
- Vaadin CDI Addon ([{{core.flow-cdi.javaVersion}}](https://github.com/vaadin/cdi/releases/tag/{{core.flow-cdi.javaVersion}})). You can use the add-on with V10+, see https://github.com/vaadin/cdi#using-with-vaadin-10 for instructions.
- Maven Plugin for Vaadin ({{platform}})
- Gradle plugin for Flow ([{{core.gradle.javaVersion}}](https://github.com/devsoap/gradle-vaadin-flow/releases/tag/{{core.gradle.javaVersion}}))
- Vaadin Multiplatform Runtime **(Prime)**
  - for Framework 7 ([{{core.mpr-v7.javaVersion}}](https://github.com/vaadin/multiplatform-runtime/releases/tag/{{core.mpr-v7.javaVersion}}))
  - for Framework 8 ([{{core.mpr-v8.javaVersion}}](https://github.com/vaadin/multiplatform-runtime/releases/tag/{{core.mpr-v8.javaVersion}}))

### Components
#### Vaadin flow components
All listed components' Java integration follow the Vaadin version [{{platform}}](https://github.com/vaadin/vaadin-flow-components/releases/tag/{{platform}})
#### Vaadin Web Components
{{components}}

### Themes
- Vaadin Lumo theme ([v{{core.vaadin-lumo-styles.jsVersion}}](https://github.com/vaadin/vaadin-lumo-styles/releases/tag/v{{core.vaadin-lumo-styles.jsVersion}}))
- Vaadin Material theme ([v{{core.vaadin-material-styles.jsVersion}}](https://github.com/vaadin/vaadin-material-styles/releases/tag/v{{core.vaadin-material-styles.jsVersion}})).

### Router
- Vaadin Router ([v{{core.vaadin-router.jsVersion}}](https://github.com/vaadin/vaadin-router/releases/tag/v{{core.vaadin-router.jsVersion}}))

### Tools
- Vaadin Designer **(Pro)** ([Release notes](https://github.com/vaadin/designer/blob/master/RELEASE-NOTES.md))
- Vaadin TestBench **(Pro)** ([{{vaadin.vaadin-testbench.javaVersion}}](https://github.com/vaadin/testbench/releases/tag/{{vaadin.vaadin-testbench.javaVersion}}))

# Getting Started with Vaadin
## App starters
The best way to get started with Vaadin is to go to [https://vaadin.com/start](https://vaadin.com/start) and pick an app template for the technology stack you’re interested in. 

### Note
Vaadin 19 starters are not available just yet in vaadin.com. You can use Vaadin 14 starter and manually change Vaadin version (see instructions below).

## Manually changing Vaadin version for Java projects

Add the following contents to your project pom.xml.
```
<dependencyManagement>
    ...
    <dependency>
        <groupId>com.vaadin</groupId>
        <artifactId>vaadin-bom</artifactId>
        <version>{{platform}}</version>
        <type>pom</type>
        <scope>import</scope>
    </dependency>
    ...
</dependencyManagement>

<repositories>
    <repository>
        <id>vaadin-prereleases</id>
        <url>https://maven.vaadin.com/vaadin-prereleases</url>
    </repository>
</repositories>

<pluginRepositories>
    <pluginRepository>
        <id>vaadin-prereleases</id>
        <url>https://maven.vaadin.com/vaadin-prereleases</url>
    </pluginRepository>
</pluginRepositories>
```

# Known Issues and Limitations

This is the prerelease version of Vaadin 19 for evaluating a number of new features and bug fixes. The API in this prerelease version is not considered final and may change based on user feedback.

## Flow
- The Template-in-Template feature has [some limitations](https://github.com/vaadin/flow/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+label%3Atemplate-in-template+)
- Links matching the context do not result in browser page load by default, instead they are handled with application routing. To opt-out, set the `router-ignore` attribute on the anchor element. This opt-out is needed for cases when native browser navigation is necessary, e. g., when [using `Anchor` to link a `StreamResource` download](https://github.com/vaadin/flow/issues/7623).

# Migrating from Vaadin 8
See [the migration guide](https://vaadin.com/docs/v10/flow/migration/1-migrating-v8-v10.html)

# Migrating from Vaadin 10-14
See [the migration guide](https://vaadin.com/docs/v14/flow/v14-migration/v14-migration-guide.html)

# Migrating from Vaadin 17
Update the Vaadin version in the build files, and check if the project is using any of the breaking changes mentioned in the 'New and Noteworthy' section above.
In addition, in the case of using the now deprecated PolymerTemplate in views, we encourage to migrate to LitTemplate.

# Reporting Issues
We appreciate if you try to find the most relevant repository to report the issue in. If it is not obvious which project to add issues to, you are always welcome to report any issue at https://github.com/vaadin/platform/issues.

A few rules of thumb will help you and us in finding the correct repository for the issue:
1) Bug tickets and enhancement requests that are specific to a certain Vaadin component should be posted in the component's Web Component repostory (e.g. https://github.com/vaadin/vaadin-button for Button).
2) Issues that are not component-specific (e.g. requests for new components) or encompass multiple components should be posted in [vaadin-flow-components](https://github.com/vaadin/vaadin-flow-components) repository. 
3) If you encounter an issue with Flow which does not seem to be related to a specific component, the problem is likely in Flow itself. The Flow repository is https://github.com/vaadin/flow
4) If you encounter an issue with Designer, the repository is https://github.com/vaadin/designer
5) If you encounter an issue with TestBench, the repository is https://github.com/vaadin/testbench
