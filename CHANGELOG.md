protostuff-1.8.1-SNAPSHOT

protostuff-1.8.0 2022-03-12
===========================
- `-Dprotostuff.runtime.preserve_null_elements=true` preserves null elements in collections/arrays.
  This property replaces `-Dprotostuff.runtime.allow_null_array_element=true`, which only applied to arrays.
  Note that this works only on the binary formats (protostuff/protobuf/graph)
- allow protostuff-runtime to work with java 9 and above
- handle invalid repeated/collection/map pojos during serialization (Issue 309)
- include class and field name in error msg for invalid repeated/collection/map pojos during serialization (Issue 309)

protostuff-1.7.4 2021-04-29
===========================
- include class and field name in error msg for invalid repeated/collection/map pojos during serialization (Issue 309)

protostuff-1.7.3 2021-04-29
===========================
- handle invalid repeated/collection/map pojos during serialization (Issue 309)

protostuff-1.7.2 2020-04-18
===========================
- Issue 273 - fix bug on custom maps without a K (Key) parameter type. Only the V (value) parameter type is declared.

protostuff-1.6.2 2019-10-07
===========================
- null elements support for pojos in object array [`8fddbd5`](https://github.com/protostuff/protostuff/commit/8fddbd526968ace00583a3abfd64b9287351cea0) (Issue 266)

protostuff-1.6.1 2019-10-04
===========================

- Added tests for io.protostuff.ProtobufOutput [`#263`](https://github.com/protostuff/protostuff/pull/263)
- Fix immutable collection or map fields deserialization issue. [`#260`](https://github.com/protostuff/protostuff/pull/260)
- RuntimeEnv.ALLOW_NULL_ARRAY_ELEMENT is invalid for IdStrategy#ARRAY_STRING_SCHEMA [`#253`](https://github.com/protostuff/protostuff/pull/253)
- test: test writeVarInt32 with large Integer [`#250`](https://github.com/protostuff/protostuff/pull/250)
- avoid use Array.get/set (JNI) to boost the performance [`#246`](https://github.com/protostuff/protostuff/pull/246)
- Use a CharSequence as a source for read/writeString [`#216`](https://github.com/protostuff/protostuff/pull/216)
- Re-use a ByteBuffer to read bytes from Input [`#215`](https://github.com/protostuff/protostuff/pull/215)
- Fix JSON deserialization of "Infinite", "-Infinite" and "NaN" [`#220`](https://github.com/protostuff/protostuff/pull/220)
- assert the returned value of writeList [`#212`](https://github.com/protostuff/protostuff/pull/212)
- Add feature to reset CodedInput object in order to avoid a new allocation for each mergeFrom [`#211`](https://github.com/protostuff/protostuff/pull/211)
- add protostuff-msgpack module [`#208`](https://github.com/protostuff/protostuff/pull/208)
- Prioritize registered pojos over maps/collections [`#201`](https://github.com/protostuff/protostuff/pull/201)
- Speedup repeated/collection fields [`#199`](https://github.com/protostuff/protostuff/pull/199)
- [maven-release-plugin] prepare for next development iteration [`d33c699`](https://github.com/protostuff/protostuff/commit/d33c6992046c6787d0768a6c9f6bf5d4d29a7348)
- https://github.com/protostuff/protostuff/issues/251 [`4a6b0d2`](https://github.com/protostuff/protostuff/commit/4a6b0d2a2f443f9407ff83ee27c656399ecf31b4)

protostuff-1.6.0 2017-07-03
===========================
- Use a CharSequence as a source for read/writeString (#216)

protostuff-1.3.3 2015-03-23
===========================

Improvements
------------

* [#105](https://github.com/protostuff/protostuff/pull/105): Add option for generating field maps with original field names `[generated code]`

Fixes
-----

* [#98](https://github.com/protostuff/protostuff/issues/98): Fix for messages with sparse/big `@Tag` values `[runtime schemas]`
* [#108](https://github.com/protostuff/protostuff/issues/108): Fix for default values in `java_bean_model` `[generated code]`
* [#107](https://github.com/protostuff/protostuff/issues/107): Getter of optional enum should return `null` if not set `[generated code]`

Compatibility notes
-------------------

* Please check https://github.com/protostuff/protostuff/issues/107 as it changes structure of the schema, generated by `java_bean`. Now default values are not applied automatically for all field types, unless default value is specified explicitly. 
If you use protobuf as a serialization format, you should always do check for `null` and treat `null` as a default value. For example, you can use Guava's utility method: `MoreObjects.firstNonNull(message.getNullableFieldValue(), DEFAULT_FIELD_VALUE)`.

protostuff-1.3.2 2015-03-01
===========================

Improvements
------------

* [#81](https://github.com/protostuff/protostuff/issues/81): add validation for @Tag annotation value, throw an IllegalArgumentException when value is out of range [protostuff-runtime]
* [#83](https://github.com/protostuff/protostuff/issues/83): add maven "Bill of Materials" module
* [#94](https://github.com/protostuff/protostuff/pull/94): add method `getProtoType` for `Field` [code generator]
* [#92](https://github.com/protostuff/protostuff/issues/92): generate `equals()` and `hashCode()` for generated messages [code generator]

protostuff-1.3.1 2015-02-12
===========================

Improvements
------------

[#86](https://github.com/protostuff/protostuff/issues/86): Configure system properties for maven plugin in the POM

Now it is possible to specify proto-compiler options directly in `pom.xml`

```xml
<plugin>
        <groupId>io.protostuff</groupId>
        <artifactId>protostuff-maven-plugin</artifactId>
        <version>${protostuff.version}</version>
        <configuration>
          <properties>
            <property>
              <name>ppc.check_filename_placeholder</name>
              <value>true</value>
            </property>
          </properties>
          <protoModules>
...
```

Fixes
-----

[#84](https://github.com/protostuff/protostuff/issues/84): Value of `@Generated` annotation is not valid string [code generator]
[#90](https://github.com/protostuff/protostuff/pull/90): 
 * fixed issue with relative template file location (`<output>` maven plugin option) in multi-module projects
 * fixed `PluginProtoCompiler` behavior when `ppc.check_filename_placeholder` is enabled, https://code.google.com/p/protostuff/issues/detail?id=166  

protostuff-1.3.0 2015-01-13
===========================

Improvements
------------

* [#74](https://github.com/protostuff/protostuff/pull/74): Switch to com.fasterxml.jackson v2.4.4
* [#79](https://github.com/protostuff/protostuff/issues/79): Add `@Generated` annotation to generated classes


Fixes
-----

* [#58](https://github.com/protostuff/protostuff/issues/58): Do not wrap lists into `Collections.unmodifiableList(source)` (code generated by `java_bean` template)


protostuff-1.2.0 2014-12-15
===========================

Improvements
------------

* [#25](https://github.com/protostuff/protostuff/issues/25): Added `@Tag` support for enums in `protostuff-runtime` 
* [#32](https://github.com/protostuff/protostuff/issues/32): Added support for messages without fields (empty messages) 
* [#35](https://github.com/protostuff/protostuff/pull/35): Added support for RPC service code generation. [Example](https://github.com/kshchepanovskyi/protostuff-rpc-example).
* [#38](https://github.com/protostuff/protostuff/pull/38): Added ability to import proto in multi-module project. [Example](https://github.com/kshchepanovskyi/protostuff-multimodule-example).

Fixes
-----

* [#34](https://github.com/protostuff/protostuff/issues/34): Fixed issue with CESU-8 charset and Java 8.

Compatibility
-------------

* [#29](https://github.com/protostuff/protostuff/issues/29): The minimum requirement for Java has now been raised to Java SE 7.
* [#36](https://github.com/protostuff/protostuff/issues/36): Move `protostuff-me` to separate project.

protostuff-1.1.0 2014-10-06
===========================

+ NOTE: The 1.1.x versions will be not be wire-compatible with the ff:
  - protostuff-runtime-1.0.x
  - protostuff-xml-1.0.x
+ Issue 161: Optimize ProtobufOutput for small nested messages (max size of 127)
+ Issue 157: ConcurrentLinkedDeque support
+ Issue 156: Support for newing object instances on Android 4.3+ devices
  - thanks to eedzjee
+ Issue 153: YamlOutput bug on repeated message fields
+ Issue 151: optimize xml format
+ Issue 141: protostuff ser/der can not keep order of elements in an array which contain null value
  - thanks to lzh0379
+ Issue 119: Reflection-based array operations are rather expensive

protostuff-1.0.8 2013-12-10
===========================

+ Issue 140: Multiple runtime schema contexts (IdStrategy groups)
+ new protostuff-runtime-view module
  - select fields to include on ser/deser, without re-creating the expensive runtime fields.
+ Issue 139: Add functionality to load protobuf schema from Reader
+ Issue 138: CodedIpnut.skipRawBytes() incorrectly updates totalBytesRetired when going outside of its buffer.
  - thanks to Max Lanin
+ Issue 135: PluginProtoCompiler throws IllegalStateException when one of the rules (message_block, enum_block) is missing
+ Issue 133: When the varint of large strings (2kb or more) are serialized, unnecessary bytes are written
  A 2kb string previously needed 3 bytes for its varint.
  Now anything under 16kb will only need 2 bytes.
  This is a bug that was overlooked but doesn't have major side effects because of the way varint encoding works.
+ Issue 131: option can't be used as a field name in maven-plugin
+ Issue 129: Default value of optional bool properties is ignored.
+ Issue 128: Maven-Plugin fails for multi-module projects
+ added enums_by_name compiler option for java_v2protoc_schema (thanks to vitalyper)
+ Issue 124: proto-parser throws NPE when an annotation on a field contains a reference
+ update jackson-core-asl to 1.9.13
+ update woodstox-core-asl to 4.1.3

protostuff-1.0.7 2012-05-14
===========================

+ bugfix: an abstract class mapped to a single impl was not honored (bug introduced on 1.0.6)

protostuff-1.0.6 2012-05-14
===========================

+ allow @Tag annotations to override the field name
  - E.g @Tag(value=1, alias="foo")
  - useful for non-binary formats like json/xml/yaml
+ added Delegate, which handles ser/deser for:
  - singletons
  - pojos with no fields
  - pojos that should not be merged
  - could be used to encode a type to a byte array and write it (for example packing an int[] to a byte[])
+ added @Morph field annotation, which overrides:
  -Dprotostuff.runtime.morph_non_final_pojos
  -Dprotostuff.runtime.morph_collection_interfaces (new)
  -Dprotostuff.runtime.morph_map_interfaces (new)
+ Issue 115: protostuff has problem to serialize java.lang.Throwable Object
+ Issue 120: Add serialization support for empty/singleton/synchronized/unmodifiable/checked collection/set/sortedset/list/map/sortedmap
+ Issue 118: Doc improvement for the compiler help message
+ Issue 104: 2 new compilers: proto_extender, java_bean_model (by Ivan Prisyazhniy and Igor Scherbak)
+ Issue 114: Allow collection/map registration on DefaultIdStrategy
+ Issue 111: NumericIdStrategy fails to use the enum ids when the field is an enum array
+ Issue 110: protostuff has problem serilize java.lang.Class Object
+ Issue 108: Ignore null values in json parser
  * removes recursion and uses a loop instead

protostuff-1.0.5 2012-03-31
===========================

+ Issue 107: Fields that are interfaces are not being serialized correctly if assigned an enum/boxed primitive type at runtime
  To optimize polymorphic ser/deser, use abstract classes or atleast declare the base abstract class.
+ add support for annotations on protostuff-runtime to have explicit control of field numbers (patch by Brice Jaglin).
  Annotate all non-transient/non-static fields with @Tag(x) or none at all (all or nothing).
+ Issue 77: RuntimeSchema.getSchema on Android and Server (the solution is to use @Tag annotations)
+ Issue 86: Is RuntimeSchema.createFrom safe (the solution is to use @Tag annotations)
+ Issue 106: Use Double.doubleToRawLongBits (was Double.doubleToLongBits) on serialization (protostuff-core)
  * Not applicable to protostuff-me since the method Double.doubleToRawLongBits does not exist on j2me api
+ new protostuff-runtime-registry module (compact ids for your polymorphic pojos)
+ Issue 105: ObjectSchema needs to check clazz.getSuperclass().isEnum() to detect complex enums
+ Issue 88: Add support for transparent handling of non-standard collections
+ Issue 96: user definable mapping: FQNC's --> integer, for serialized stream size-reduction (thanks to Leo Romanoff)
+ Issue 103: Deserialize failed when reading objects from ObjectInput/DataInput
+ Issue 101: Improve ByteString.equals
+ allow message/enum references on options and annotations (proto-parser).
+ add "cache_protos" config (cache/re-use protos being imported/loaded by multiple modules)
+ Issue 94: IllegalArgumentException thrown when instantiating a non-public class
+ Issue 93: Add runtime option to always use the constructor from sun reflection factory
+ Issue 92: [protostuff-me] Preverification fails (patch by thierry.monney)
+ Issue 91: Generated J2ME code not is not compatible

protostuff-1.0.4 2011-10-24
===========================

+ Issue 90: byte arrays on protostuff-runtime were not treated as scalar fields
            Best to update to this version for performance reasons.
            If you have existing data that came from a pojo with byte[] fields, it will not be compatible on deser.
            You can safely update the data by deserializing with the old protostuff from a different classloader 
            and writing it back again using the new protostuff on another classloader.

protostuff-1.0.3 2011-10-22
===========================

+ Issue 89: graph serialization bug on IdentityHashMap and EnumMap
+ Issue 87: EnumSet and EnumMap without generics are not handled
+ Issue 85: graph serialization bug (protostuff-runtime) on collections/map without generics and dynamic objects

protostuff-1.0.2 2011-09-12
===========================

+ add protostuff-uberjar (osgi stuff from Thomas Kock)
+ Issue 83: Kvp input does not properly handle empty strings and misreported size
+ Issue 82: Serializing repeated fields on protostuff-runtime needs a null-check to only serialize non-nulls.
+ Issue 81: Xml input does not check required fields when the nested message is not empty.
+ Issue 80: Yaml does not handle polymorphic/cyclic serialization
+ Issue 79: Provide support for options in messages and enums
+ Issue 78: Field option missing on message fields (thanks to robert.herschke.de)
+ Issue 76: The protostuff compiler does not detect duplicate service/message/enum
+ update jackson to 1.7.9

protostuff-1.0.1 2011-07-13
===========================

+ new protostuff-me module (for j2me by Michael Donohue)
+ new protostuff-runtime-md module (for modern mobile devices like android and kindle)
  api+core works fine but this is for those who prefer runtime schemas.
+ Issue 73: Remove unused enum default value from java_bean generated code
+ Issue 70: Use FQCN everywhere in classes generated by java_v2protoc_schema
+ Issue 69: Maven plugin to attach generated source directory to the project compile source roots
+ Issue 68: RuntimeSchema AccessControlException on amazon kindle
+ Issue 67: RuntimeSchema.getSchema on Android (thanks to matyas.bene)
+ Issue 66: static keyword missing on classes generated by java_v2protoc_schema
+ Issue 64: Merge method for json protobuf classes
+ Issue 62: IOUtil.mergeDelimitedFrom() reports truncated message on stream EOF reached
+ Issue 58: Compilation issues when the projects are loaded.
+ tiny optimizations for protostuff-graph
+ allow protostuff-runtime to use simple reflections or sun.misc.Unsafe(now the default scheme).
+ improve streaming support for large strings
+ update jackson-core-asl to 1.7.7
+ fixed protostuff-parser bug on handling int/double annotation attributes.

protostuff-1.0.0 2011-02-15
===========================

+ Issue 57: Add proto_path as a system property read by protostuff-compiler to load imported protos
+ add smile format
+ update jackson to 1.7.3
+ Issue 56: Signed int64 is not correctly serialized (zigzag encoding missing)
+ Issue 51: Compiler option to use primitive numbers if the field is optional
+ Issue 49: protostuff-maven-plugin:Incorrect relative path for <output> from super pom
+ Issue 54: StackOverflow using RuntimeSchema.getSchema()
+ Issue 53: UUIDs cannot be used with RuntimeSchemas
+ Issue 55: Optimize protostuff-runtime serialization of arrays by writing the length first (order dependent)
+ Issue 31: ProtoStuffRuntime cannot handle different subclasses
+ Issue 29: Empty list turns into null after serialization/deserialization
+ Issue 46: RuntimeSchema.getSchema() throws NPE on fields with type Object
+ Issue 48: Polymorphic serialization support for json and xml
+ Issue 52: Allow skipping constructor on immutable objects (fields marked final)
+ LinkedBuffer re-use for JsonIOUtil read/write operations on streams.
+ Issue 50: Xml deser does not handle empty messages well
+ minor xml optimizations
+ Issue 45: Double-checked locking concern
+ Issue 47: IllegalAccessException in when accessing a private Date field with RuntimeSchema
+ add protostuff-collectionschema (jdk standard collections support - map,list,set,queue,deque,etc)
+ Issue 43: Inheritance support for non-abstract base types

protostuff-1.0.0.M7 2011-01-20
==============================

+ add ser/deser support for object graphs (cyclic references/dependencies)
+ Issue 42: Support for Self Referential Classes
+ Issue 41: Support for polymorphic ser/deser for protostuff-runtime
+ Issue 40: ArrayIndexOutOfBoundsException when using streaming mulitple large delimited utf8 strings that exceeds the buffer size.
+ update jackson to 1.7.1
+ api for re-using the LinkedBuffer as a read-only buffer
+ add protostuff-kvp module
+ Issue 39: The field options (other than default) are ignored by the parser
+ add support for annotations on proto files (extra metadata for better code generation)
+ Issue 38: Parser: cannot import more than one .proto file from the same package (patch by avaskys)
+ add support for java.util.Date in protostuff-runtime

protostuff-1.0.0.M6 2010-10-28
==============================

+ Backward-forward compatibility support for runtime schemas via append-only fields in the pojo.
  To add new fields, append the field in the declaration.  To remove existing fields, annotate with @Deprecated.
+ Issue 37: The proto parser doesn't parse extensions without ranges
+ Issue 36: Incorrect deserialization when ProtobufIOUtil merges from InputStream
+ Issue 35: Native methods for repeated fields (patch by nordlig.ulv)
+ Issue 34: Allow schema generated from protostuff-runtime to write enums by their name

protostuff-1.0.0.M5 2010-10-12
==============================

+ add IO pipes w/c can transfer/transcode streams efficiently.
+ full streaming capability on protostuff format.
+ update jackson-core-asl to 1.6.1
+ add JsonXOutput for efficient writing of numeric keys and pre-encoded utf8 strings.
+ add base64 encoding/decoding support in protostuff-api
+ Issue 33: GWT json compiler produces unnecessary line wrap
+ IOUtil is no longer publicly accessible. (use ProtobufIOUtil or ProtostuffIOUtil)

protostuff-1.0.0.M4 2010-09-14
==============================

+ Issue 28: Class member with signature of interface causes NullPointerException
+ Issue 27: ArrayIndexOutOfBoundsException in StringSerializer.writeUTF8 (patch by Tim Underwood)
+ Add support for BigInteger and BigDecimal in protostuff-runtime
+ Issue 26: Bug in the reflection compiler with nested protobuf types (patch by Joseph Gentle)
+ Issue 25: Allow generating code for message extensions (patch by Philippe Laflamme)
+ Issue 5: Ignore "target" working directories in Subversion

protostuff-1.0.0.M3 2010-07-10
==============================

+ faster utf8 string serialization
+ write operations on IOUtil now require a buffer as an extra arg.
  This allows the developer to determine the appropriate buffer size needed for a particular message (to avoid buffer allocation overhead).
  The LinkedBuffer can be re-used by calling LinkedBuffer.clear() ... w/c is applicable to application/thread-local/network buffers.
+ added protostuf-yaml for yaml serialization (zero-copy capable).
+ Issue 24: JsonInput not able to skip repeated scalar fields that are unknown
+ support serializing Map fields via the MapSchema.
+ make Schema.typeClass() return the super type.
+ Issue 23: Validation missing (for required fields) when nested messages are "group_encoded"

protostuff-1.0.0.M2 2010-06-22
==============================

+ more IO optimizations
+ Issue 22: Enable parsing of service/rpc in proto for code generation
+ Issue 21: Support java-style compilation mode where imported messages do not need to be referenced by full name
+ Issue 20: Compiler throws NPE if no package defined in proto file 
+ added protostuff-api (protostuff-core, protostuff-json and protostuff-xml will only contain their respective IO impl).
+ added a runtime option for nested messages to be "group-encoded" for more efficient serialization. (especially for rpc).
+ added an abstract helper class CustomSchema to easily customize how messages can be read/written and for adding filters/hooks as well.
+ added messageName() and messageFullName() methods to the schema to support full xml serialization of existing C++ protoc messages.
  This also enables aliasing of the message names (especially for xml) by overriding the messageName() method.
+ added protostuff-xml for fast xml ser/deser via stax api.

protostuff-1.0.0.M1 2010-05-20
==============================

+ completed Issue 18: Generated GWT Protobuffers - base class, name
+ fixed Issue 17: trying to compile google/protobuf/descriptor.proto from protobuf-2.3.0
+ fixed Issue 15: JsonIOUtil.writeListTo fails when inner messages contain repeated fields
+ completed Issue 14: Allow packages to be overriden via compile time options
+ completed Issue 13: Allow unknown scalar fields to be ignored when parsing json-encoded messages
+ completed Issue 12: Add support for protobuf enums on GWT overlays hosted mode
+ completed Issue 11: Add serialization method (stringify) for GWT overlay types
+ fixed Issue 3: JSON parser converts null values to the string "null"
+ fixed Issue 10: JsonOutput bug when writing a message that contains an inner message with repeated fields
+ completed Issue 8: Use the default values of the optional fields of gwt-overlays
+ completed Issue 9: If enum's default value is not specified, it should be the first value listed in the enum's type definition
+ completed Issue 7: Add optional clear methods on code compiled to gwt_overlay
+ fixed Issue 4: .proto files that use "import" create non-compilable Java files
+ completed Issue 6: Support the header: syntax = "proto2"; (patch by J.D. Zamfirescu)
+ fixed Issue 2: Wrong enum type in generated code of GWT overlays
+ fixed benchmark deser bug on protostuff-json (duplicate parser created)

protostuff-1.0.0.M0 2009-10-24
==============================

+ code generator for json, numeric_json, gwt_json, gwt_numeric_json
+ maven archetypes for quick start and rapid development
+ benchmark module to relatively compare with protobuf
