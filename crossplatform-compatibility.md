# Cross-Platform Compatibility

The purpose of this document is to share the plans on how we're going to maintain cross-platform compatibility.

## Prioritization

Our goal for this project is to support all platforms works with .NET Core.

## Guidelines

Here are the high level guidelines:

* **Do not** use APIs of technologies considered/marked as deprecated or obsolote.
* **Consider** porting APIs even if considered legacy, problematic, or otherwise inadequate.
* **Do** factor assemblies appropriately in order to preserve the componentization, specifically:
	- **Do not** expose external dependencies from third party libraries.
	- **Do not** expose Windows-only technologies in otherwise fully portable assemblies.

## Known Deprecated/Obsolote .NET features

Technology                 | Reason                    |More information
---------------------------|---------------------------|------------------------
AppDomains                 | Unsupported in .NET Core  | [Details](#app_domains)
Remoting                   | Unsupported in .NET Core  | [Details](#remoting)
Binary Serialization       | Unsupported in .NET Core  | [Details](#binary-serialization)
Code Access Security (CAS) | Unsupported in .NET Core  | [Details](#code-access-security-cas)
Security Transparency      | Unsupported in .NET Core  | [Details](#security-transparency)

### App Domains

**Justification**. AppDomains require runtime support and are generally quite expensive. While still implemented by CoreCLR it's not available in .NET Native and we don't plan on adding this capability.

**Replacement**. AppDomains were used for different features; for isolation we recommend processes and/or containers.

### Remoting

**Justification**. The idea of .NET remoting -- which is transparent remote procedure calls -- has been identified as a problematic architecture. Outside of that realm, it's also used for cross AppDomain communication which is no longer supported. On top of that, remoting requires runtime support and is quite heavyweight.

**Replacement**. For communication across processes, inter-process communication (IPC) should be used, such as pipes or memory mapped files. Across machines, you should use a network based solution, preferably a low-overhead plain text protocol such as HTTP.

### Binary Serialization

**Justification**. After a decade of servicing we've learned that serialization is incredibly complicated and a huge compatibility burden for the types supporting it. Thus, we made the decision that serialization should be a protocol implemented on top of the available public APIs. However, binary serialization requires intimate knowledge of the types as it allows to serialize object graphs including private state.

**Replacement**. Choose the serialization technology that fits your goals for formatting and footprint. Popular choices include data contract serialization, XML serialization, JSON.NET, and protobuf-net.

### Code Access Security (CAS)

**Justification**. Sand-boxing, i.e. relying on the runtime or the framework to constrain which resources a managed application can run, is considered a non-goal for .NET Core. We've already state previously that relying on sand-boxing for security reasons isn't an approach we're feeling comfortable with; there are simply too many pieces in object oriented framework that can result in elevation of privileges. Thus we don't treat CAS as security boundary anymore. On top of that, it makes the implementation more complicated and often has performance implications for the happy path.

**Replacement**. Use operating system provided security boundaries, such as user accounts for running processes with the least set of privileges.

### Security Transparency

**Justification**. Similar to CAS, this feature allows separating sand-boxed code from security critical code in a declarative fashion. This feature was heavily used by Silverlight. 

**Replacement**. Use operating system provided security boundaries, such as user accounts for running processes with the least set of privileges.
