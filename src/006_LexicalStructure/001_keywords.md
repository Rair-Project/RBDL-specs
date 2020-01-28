## Keywords

RBDL has two sets of keywords: The first set is functional keywords. These keywords **MUST** be only used in their specific context. The second set is non-functional keywords. Non-functional keywords **MUST NOT** be used anywhere in a *well-formed document*. The rationale is that non-functional keywords are reserve keyword in one or more
*target language*.


### Functional Keywords

```
bool    enum    false   true    struct
```

### Non-functional Keywords

```
_               _Alignas        _Alignof            _Atomic _Bool   _Complex
_Generic        _Imaginary      _Noreturn           _Static         _Thread_local
__ENCODING      __FILE__        __LINE__            __func__        _assert
abstract        alias           alignas             alignof         and
and_eq          as              asm                 assert          async
auto            await           base                become          BEGIN
begin           bitand          bitor               boolean         box
break           byte            case                catch           char
char16_t        char32_t        checked             class           compl
const           const_cast      constexpr           continue        crate
decimal         decltype        def                 default         defined
del             delegate        delete              do              double
dyn             dynamic_cast    elif                else            elsif
END             end             ensure              enumerate       event
except          explicit        export              extends         extern
False           final           finally             fixed           float
fn              for             foreach             friend          from
global          goto            if                  impl            implements
implicit        import          in                  inline          instanceof
int             interface       internal            is              lambda
let             lock            long                loop            macro
match           mod             module              move            mut
mutable         namespace       native              new             next
nil             noexcept        None                nonlocal        not
not_eq          null            nullptr             object          operator
or              or_eq           out                 override        package
params          pass            priv                private         protected
pub             public          raise               readonly        redo
ref             register        reinterpret_cast    rescue          restrict
retry           return          sbyte               sealed          Self
self            short           signed              sizeof          stackalloc
static          static_assert   static_cast         strictfp        string
super           switch          synchronized        template        then
this            thread_local    throw               throws          trait
transient       True            try                 type            typedef
typeid          typename        typeof              uint            ulong
unchecked       undef           union               unless          unsafe
unsigned        unsized         until               use             ushort
using           virtual         void                volatile        wchar_t
when            where           while               with            xor
xor_eq          yield
```