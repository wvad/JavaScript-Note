# Ordinary Object
普通のオブジェクト。

## Internal Slots
|  Internal Slot   |      Type      |                      説明              |
| ---------------- | -------------- | -------------------------------------- |
| \[\[Prototype]]  | null \| object | オブジェクトのプロトタイプ                |
| \[\[Extensible]] |    boolean     | オブジェクトがプロパティーを追加できるか否か |

## Internal methods
[Table 4: Essential Internal Methods](https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#table-essential-internal-methods)  
[Ordinary Object Internal Methods](https://tc39.es/ecma262/multipage/ordinary-and-exotic-objects-behaviours.html#sec-ordinary-object-internal-methods-and-internal-slots-getprototypeof)



# ECMAScript Function Object
Ordinary Object が持っている Internal Slot, Internal Method の他に、以下の通り、関数オブジェクト独自の Internal Slot, Internal Method も持つ。

## Internal Slots
|          Internal Slot          |              Type              |                  説明                  |
| ------------------------------- | ------------------------------ | -------------------------------------- |
|         \[\[Prototype]]         |         null \| object         | オブジェクトのプロトタイプ                |
|        \[\[Extensible]]         |            boolean             | オブジェクトがプロパティーを追加できるか否か |
|        \[\[Environment]]        | [Environment Record](https://tc39.es/ecma262/multipage/executable-code-and-execution-contexts.html#sec-environment-records) | The [Environment Record](https://tc39.es/ecma262/multipage/executable-code-and-execution-contexts.html#sec-environment-records) that the function was closed over. Used as the outer environment when evaluating the code of the function |
|    \[\[PrivateEnvironment]]     | [PrivateEnvironment Record](https://tc39.es/ecma262/multipage/executable-code-and-execution-contexts.html#privateenvironment-record) \| null | The [PrivateEnvironment Record](https://tc39.es/ecma262/multipage/executable-code-and-execution-contexts.html#privateenvironment-record) for [Private Name](https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#sec-private-names)s that the function was closed over. null if this function is not syntactically contained within a class. Used as the outer PrivateEnvironment for inner classes when evaluating the code of the function |
|     \[\[FormalParameters]]      | [Parse Node](https://tc39.es/ecma262/multipage/notational-conventions.html#sec-syntactic-grammar) | The root parse node of the source text that defines the function's formal parameter list |
|      \[\[ECMAScriptCode]]       | [Parse Node](https://tc39.es/ecma262/multipage/notational-conventions.html#sec-syntactic-grammar) | The root parse node of the source text that defines the function's body |
|      \[\[ConstructorKind]]      |       #base \| #derived        | Whether or not the function is a derived class constructor |
|           \[\[Realm]]           | [Realm Record](https://tc39.es/ecma262/multipage/executable-code-and-execution-contexts.html#realm-record) | The [realm](https://tc39.es/ecma262/multipage/executable-code-and-execution-contexts.html#realm) in which the function was created and which provides any intrinsic objects that are accessed when evaluating the function |
|      \[\[ScriptOrModule]]       | [Script Record](https://tc39.es/ecma262/multipage/ecmascript-language-scripts-and-modules.html#script-record) \| [Module Record](https://tc39.es/ecma262/multipage/ecmascript-language-scripts-and-modules.html#sec-abstract-module-records) | The script or module in which the function was created |
|         \[\[ThisMode]]          | #lexical \| #strict \| #global | Defines how this references are interpreted within the formal parameters and code body of the function. lexical means that this refers to the this value of a lexically enclosing function. strict means that the this value is used exactly as provided by an invocation of the function. global means that a this value of undefined or null is interpreted as a reference to the [global object](https://tc39.es/ecma262/multipage/global-object.html#sec-global-object), and any other this value is first passed to [ToObject](https://tc39.es/ecma262/multipage/abstract-operations.html#sec-toobject) |
|          \[\[Strict]]           |             boolean            | true if this is a strict function, false if this is a non-strict function |
|        \[\[HomeObject]]         |             object             | If the function uses super, this is the object whose \[\[GetPrototypeOf]] provides the object where super property lookups begin |
|        \[\[SourceText]]         | Sequence\<Unicode Code Point>  | The source text that defines the function |
|          \[\[Fields]]           | [List](https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#sec-list-and-record-specification-type)\<[ClassFieldDefinition Record](https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#sec-classfielddefinition-record-specification-type)> | If the function is a class, this is a list of Records representing the non-static fields and corresponding initializers of the class |
|      \[\[PrivateMethods]]       | [List](https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#sec-list-and-record-specification-type)\<[PrivateElement](https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#sec-privateelement-specification-type)> | If the function is a class, this is a list representing the non-static private methods and accessors of the class |
| \[\[ClassFieldInitializerName]] | string \| symbol \| [Private Name](https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#sec-private-names) \| empty | If the function is created as the initializer of a class field, the name to use for NamedEvaluation of the field; empty otherwise |
|    \[\[IsClassConstructor]]     |             boolean            | Whether the function is a class constructor. (If true, invoking the function's [[Call]] will immediately throw a TypeError exception) |

## Additional internal methods
[Table 5: Additional Essential Internal Methods of Function Objects](https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#table-additional-essential-internal-methods-of-function-objects)  
[Function Object Internal Methods](https://tc39.es/ecma262/multipage/ordinary-and-exotic-objects-behaviours.html#sec-ecmascript-function-objects-call-thisargument-argumentslist)



# Built-in Function Object
The built-in function objects defined in this specification may be implemented as either ECMAScript function objects whose behaviour is provided using ECMAScript code or as implementation provided function exotic objects whose behaviour is provided in some other manner.  

## Internal Slots
In addition to Internal Slots of ECMAScript Function Object,
|   Internal Slot   |  Type  |    説明     |
| ----------------- | ------ | ---------- |
| \[\[InitialName]] | string | 関数の初期名 |

## Additional internal methods
[Table 5: Additional Essential Internal Methods of Function Objects](https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#table-additional-essential-internal-methods-of-function-objects)  
[Built-in Function Object Internal Methods](https://tc39.es/ecma262/multipage/ordinary-and-exotic-objects-behaviours.html#sec-built-in-function-objects-call-thisargument-argumentslist)



# Bound Function Exotic Object
Function#bind で作られた関数オブジェクト。  
別の関数オブジェクトをラップする Exotic Object。  
関数として呼び出し可能で、呼び出すと、通常、ラップされた関数が呼び出される。  

## Internal Slots
|       Internal Slot       |      Type      |                      説明                      |
| ------------------------- | -------------- | ---------------------------------------------- |
|      \[\[Prototype]]      | null \| object | オブジェクトのプロトタイプ                        |
|     \[\[Extensible]]      |    boolean     | オブジェクトがプロパティーを追加できるか否か         |
| \[\[BoundTargetFunction]] |    function    | ターゲットの関数                                 |
|      \[\[BoundThis]]      |       any      | ターゲットを呼び出すときに this として常に渡される値 |
|   \[\[BoundArguments]]    | [List](https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#sec-list-and-record-specification-type)\<any> | ターゲットへの呼び出しの最初の引数として要素が使用される値のリスト。 |

## Additional internal methods
[Table 5: Additional Essential Internal Methods of Function Objects](https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#table-additional-essential-internal-methods-of-function-objects)  
[Bound Function Exotic Object Internal Methods](https://tc39.es/ecma262/multipage/ordinary-and-exotic-objects-behaviours.html#sec-bound-function-exotic-objects-call-thisargument-argumentslist)



# Array Exotic Object
Arrayオブジェクト。

## Internal Slots
|  Internal Slot   |      Type      |                      説明              |
| ---------------- | -------------- | -------------------------------------- |
| \[\[Prototype]]  | null \| object | オブジェクトのプロトタイプ                |
| \[\[Extensible]] |    boolean     | オブジェクトがプロパティーを追加できるか否か |

## Internal method override
- \[\[DefineOwnProperty]] (P, Desc)



# Arguments Exotic Object
Argumentsオブジェクト。

## Internal Slots
|   Internal Slot    |  Type          |                             説明                               |
| ------------------ | -------------- | ------------------------------------------------------------- |
|  \[\[Prototype]]   | null \| object | オブジェクトのプロトタイプ                                        |
|  \[\[Extensible]]  |    boolean     | オブジェクトがプロパティーを追加できるか否か                         |
| \[\[ParameterMap]] |     object     | 引数バインディングへの引数オブジェクトの対応を指定するためのデバイス(?) |

## Internal method overrides
- \[\[GetOwnProperty]] (P)
- \[\[DefineOwnProperty]] (P, Desc)
- \[\[Get]] (P, Receiver)
- \[\[Set]] (P, V, Receiver)
- \[\[Delete]] (P)



# Integer-Indexed Exotic Object
TypedArrayオブジェクト。

## Internal Slots
|      Internal Slot      |        Type        |                 説明                   |
| ----------------------- | ------------------ | -------------------------------------- |
|     \[\[Prototype]]     |   null \| object   | オブジェクトのプロトタイプ                |
|     \[\[Extensible]]    |      boolean       | オブジェクトがプロパティーを追加できるか否か |
| \[\[ViewedArrayBuffer]] |    ArrayBuffer     | 配列ビューの表示対象となるArrayBuffer      |
|    \[\[ArrayLength]]    |       number       | 配列長                                  |
|    \[\[ByteOffset]]     |       number       | 配列ビューが表示するメモリ範囲のオフセット   |
|    \[\[ByteLength]]     |       number       | 配列ビューが表示するメモリ範囲の長さ        |
|    \[\[ContentType]]    | #BigInt \| #Number | 要素の値の型                             |
|  \[\[TypedArrayName]]   |       string       | 配列ビューの型名                         |

## Internal method overrides
- \[\[GetOwnProperty]] (P)
- \[\[HasProperty]] (P)
- \[\[DefineOwnProperty]] (P, Desc)
- \[\[Get]] (P, Receiver)
- \[\[Set]] (P, V, Receiver)
- \[\[Delete]] (P)
- \[\[OwnPropertyKeys]] ()



# Module Namespace Exotic Object
ESモジュールのエクスポート用の特殊なオブジェクト。  

## Internal Slots
|  Internal Slot   |      Type      |                 説明                   |
| ---------------- | -------------- | -------------------------------------- |
| \[\[Prototype]]  | null \| object | オブジェクトのプロトタイプ                |
| \[\[Extensible]] |    boolean     | オブジェクトがプロパティーを追加できるか否か |
| \[\[Module]]  |  [Module Record](https://tc39.es/ecma262/multipage/ecmascript-language-scripts-and-modules.html#sec-abstract-module-records) | この名前空間をエクスポートするモジュールレコード |
| \[\[Exports]] | [List](https://tc39.es/ecma262/multipage/ecmascript-data-types-and-values.html#sec-list-and-record-specification-type)\<string> | エクスポートされた名前の文字列リスト。Array#sortと同じアルゴリズムで並べ替えられる |

## Internal method overrides
- \[\[GetPrototypeOf]] ()
- \[\[SetPrototypeOf]] (V)
- \[\[IsExtensible]] ()
- \[\[PreventExtensions]] ()
- \[\[GetOwnProperty]] (P)
- \[\[DefineOwnProperty]] (P, Desc)
- \[\[HasProperty]] (P)
- \[\[Get]] (P, Receiver)
- \[\[Set]] (P, V, Receiver)
- \[\[Delete]] (P)
- \[\[OwnPropertyKeys]] ()



# Immutable Prototype Exotic Object
Object.prototype などの、プロトタイプを変えられない特殊なオブジェクト。  

## Internal Slots
|  Internal Slot   |      Type      |                      説明              |
| ---------------- | -------------- | -------------------------------------- |
| \[\[Prototype]]  | null \| object | オブジェクトのプロトタイプ                |
| \[\[Extensible]] |    boolean     | オブジェクトがプロパティーを追加できるか否か |

## Internal method override
- \[\[SetPrototypeOf]] (V)


# Proxy Object
Proxy オブジェクト。  

## Internal Slots
|   Internal Slot    |  Type  |                      説明              |
| ------------------ | ------ | -------------------------------------- |
| \[\[ProxyHandler]] | object | どの操作を傍受するか、また傍受された操作をどのように再定義するかを定義するオブジェクト |
| \[\[ProxyTarget]]  | object | プロキシを設定する元のオブジェクト |

## Internal method overrides
- \[\[GetPrototypeOf]] ()
- \[\[SetPrototypeOf]] (V)
- \[\[IsExtensible]] ()
- \[\[PreventExtensions]] ()
- \[\[GetOwnProperty]] (P)
- \[\[DefineOwnProperty]] (P, Desc)
- \[\[HasProperty]] (P)
- \[\[Get]] (P, Receiver)
- \[\[Set]] (P, V, Receiver)
- \[\[Delete]] (P)
- \[\[OwnPropertyKeys]] ()
- \[\[Call]] (thisArgument, argumentsList)
- \[\[Construct]] (argumentsList, newTarget)
