---
title: Interfejs API Microsoft. VisualStudio. TestTools. CppUnitTestFramework
ms.date: 09/27/2019
ms.topic: reference
ms.author: corob
manager: jillfra
ms.workload:
- multiple
author: corob-msft
ms.openlocfilehash: 16ea629312237dd859e9eb1aad21b9b219de7229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "82109432"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Dokumentacja interfejsu API Microsoft. VisualStudio. TestTools. CppUnitTestFramework

W tym temacie wymieniono publiczne elementy członkowskie `Microsoft::VisualStudio::CppUnitTestFramework` przestrzeni nazw. Za pomocą tych interfejsów API można pisać testy jednostkowe języka C++ w oparciu o środowisko testów jednostkowych firmy Microsoft. Na końcu tematu znajduje się [przykład użycia](#example) .

Pliki nagłówka i lib znajdują się w obszarze * \<Visual Studio installation folder> \VC\Auxiliary\VS\UnitTest*.

Ścieżki nagłówka i lib są automatycznie konfigurowane w natywnym projekcie testowym.

## <a name="in-this-topic"></a><a name="In_this_topic"></a> W tym temacie

[CppUnitTest. h](#cppUnitTest_h)

- [Tworzenie klas i metod testowych](#create_test_classes_and_methods)

- [Inicjuj i oczyść](#Initialize_and_cleanup)

  - [Metody testowe](#test_methods)

  - [Klasy testowe](#test_classes)

  - [Moduły testowe](#test_modules)

- [Utwórz atrybuty testu](#create_test_attributes)

  - [Atrybuty metody testowej](#test_method_attributes)

  - [Atrybuty klasy testowej](#test_class_attributes)

  - [Atrybuty modułu testowego](#test_module_attributes)

  - [Wstępnie zdefiniowane atrybuty](#pre_defined_attributes)

    [CppUnitTestAssert. h](#cppUnitTestAssert_h)

  - [Potwierdzenia ogólne](#general_asserts)

    - [Jest równe](#general_are_equal)

    - [Nie są równe](#general_are_not_equal)

    - [Są takie same](#general_are_same)

    - [Nie są takie same](#general_are_not_same)

    - [Ma wartość null](#general_is_null)

    - [Nie ma wartości null](#general_is_not_null)

    - [Ma wartość true](#general_is_True)

    - [Ma wartość false](#general_is_false)

    - [Niepowodzenie](#general_Fail)

  - [Potwierdzenia środowisko wykonawcze systemu Windows](#winrt_asserts)

    - [Jest równe](#winrt_are_equal)

    - [Są takie same](#winrt_are_same)

    - [Nie są równe](#winrt_are_not_equal)

    - [Nie są takie same](#winrt_are_not_same)

    - [Ma wartość null](#winrt_is_null)

    - [Nie ma wartości null](#winrt_is_not_null)

  - [Potwierdzenia wyjątków](#exception_asserts)

    - [Oczekiwanie wyjątku](#expect_exception)

      [CppUnitTestLogger. h](#cppunittestlogger_h)

    - [Rejestratora](#logger)

    - [Napisz wiadomość](#write_message)

  - [Przykład użycia](#example)

## <a name="cppunittesth"></a><a name="cppUnitTest_h"></a> CppUnitTest. h

### <a name="create-test-classes-and-methods"></a><a name="create_test_classes_and_methods"></a> Tworzenie klas i metod testowych

```cpp
TEST_CLASS(className)
```

Wymagane dla każdej klasy zawierającej metody testowe. Identyfikuje element *ClassName* jako klasę testową. `TEST_CLASS` musi być zadeklarowany w zakresie przestrzeni nazw.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

Definiuje *MethodName* jako metodę testową. `TEST_METHOD` musi być zadeklarowany w zakresie klasy metody.

### <a name="initialize-and-cleanup"></a><a name="Initialize_and_cleanup"></a> Inicjuj i oczyść

#### <a name="test-methods"></a><a name="test_methods"></a> Metody testowe

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

Definiuje *MethodName* jako metodę, która jest uruchamiana przed uruchomieniem każdej metody testowej. `TEST_METHOD_INITIALIZE` można zdefiniować tylko raz w klasie testowej i musi być zdefiniowany w zakresie klasy testowej.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

Definiuje *MethodName* jako metodę, która jest uruchamiana po wykonaniu każdej metody testowej. `TEST_METHOD_CLEANUP` można zdefiniować tylko raz w klasie testowej i musi być zdefiniowany w zakresie klasy testowej.

#### <a name="test-classes"></a><a name="test_classes"></a> Klasy testowe

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

Definiuje *MethodName* jako metodę, która jest uruchamiana przed utworzeniem każdej klasy testowej. `TEST_CLASS_INITIALIZE` można zdefiniować tylko raz w klasie testowej i musi być zdefiniowany w zakresie klasy testowej.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

Definiuje *MethodName* jako metodę, która jest uruchamiana po utworzeniu każdej klasy testowej. `TEST_CLASS_CLEANUP` można zdefiniować tylko raz w klasie testowej i musi być zdefiniowany w zakresie klasy testowej.

#### <a name="test-modules"></a><a name="test_modules"></a> Moduły testowe

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

Definiuje metodę *MethodName* , która jest uruchamiana podczas ładowania modułu. `TEST_MODULE_INITIALIZE` można zdefiniować tylko raz w module testowym i musi być zadeklarowany w zakresie przestrzeni nazw.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

Definiuje metodę *MethodName* , która jest uruchamiana, gdy moduł jest zwolniony. `TEST_MODULE_CLEANUP` można zdefiniować tylko raz w module testowym i musi być zadeklarowany w zakresie przestrzeni nazw.

### <a name="create-test-attributes"></a><a name="create_test_attributes"></a> Utwórz atrybuty testu

#### <a name="test-method-attributes"></a><a name="test_method_attributes"></a> Atrybuty metody testowej

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

Dodaje atrybuty zdefiniowane z co najmniej jednym `TEST_METHOD_ATTRIBUTE` makrem do metody testowej *testMethodName*.

`TEST_METHOD_ATTRIBUTE`Makro definiuje atrybut o nazwie *AttributeName* i wartości *atrybutu AttributeValue*.

#### <a name="test-class-attributes"></a><a name="test_class_attributes"></a> Atrybuty klasy testowej

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

Dodaje atrybuty zdefiniowane z co najmniej jednym `TEST_CLASS_ATTRIBUTE` makrem do klasy testowej *testClassName*.

`TEST_CLASS_ATTRIBUTE`Makro definiuje atrybut o nazwie *AttributeName* i wartości *atrybutu AttributeValue*.

#### <a name="test-module-attributes"></a><a name="test_module_attributes"></a> Atrybuty modułu testowego

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

Dodaje atrybuty zdefiniowane z co najmniej jednym `TEST_MODULE_ATTRIBUTE` makrem do modułu testowego *testModuleName*.

`TEST_MODULE_ATTRIBUTE`Makro definiuje atrybut o nazwie *AttributeName* i wartości *atrybutu AttributeValue*.

#### <a name="pre-defined-attributes"></a><a name="pre_defined_attributes"></a> Wstępnie zdefiniowane atrybuty

Te wstępnie zdefiniowane makra atrybutów są udostępniane jako wygoda dla typowych przypadków. Mogą zostać zastąpione przez makro `TEST_METHOD_ATTRIBUTE` opisane powyżej.

```cpp
TEST_OWNER(ownerAlias)
```

Definiuje `TEST_METHOD_ATTRIBUTE` nazwę `Owner` i wartość atrybutu *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

Definiuje `TEST_METHOD_ATTRIBUTE` nazwę `Description` i wartość atrybutu *Description*.

```cpp
TEST_PRIORITY(priority)
```

Definiuje `TEST_METHOD_ATTRIBUTE` nazwę `Priority` i wartość atrybutu *priorytet*.

```cpp
TEST_WORKITEM(workitem)
```

Definiuje `TEST_METHOD_ATTRIBUTE` wartość przy użyciu nazwy `WorkItem` i wartości atrybutu elementu *roboczego*.

```cpp
TEST_IGNORE()
```

Definiuje `TEST_METHOD_ATTRIBUTE` przy użyciu nazwy `Ignore` i wartości atrybutu `true` .

## <a name="cppunittestasserth"></a><a name="cppUnitTestAssert_h"></a> CppUnitTestAssert. h

### <a name="general-asserts"></a><a name="general_asserts"></a> Potwierdzenia ogólne

#### <a name="are-equal"></a><a name="general_are_equal"></a> Jest równe
Sprawdź, czy dwa obiekty są równe

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa podwojone są równe

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa wartości zmiennoprzecinkowe są równe

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa znaki * są równe

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa w_char * ciągi są równe

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-equal"></a><a name="general_are_not_equal"></a> Nie są równe
Sprawdź, czy dwa podwójnej precyzji nie są równe

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa wartości zmiennoprzecinkowe nie są równe

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa znaki * nie są równe

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa w_char * ciągi nie są równe

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa odwołania nie są równe na podstawie operatora = =.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-same"></a><a name="general_are_same"></a> Są takie same
Sprawdź, czy dwa odwołania odwołują się do tego samego wystąpienia obiektu (tożsamości).

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-same"></a><a name="general_are_not_same"></a> Nie są takie same
Sprawdź, czy dwa odwołania nie odwołują się do tego samego wystąpienia obiektu (tożsamości).

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-null"></a><a name="general_is_null"></a> Ma wartość null
Sprawdź, czy wskaźnik ma wartość NULL.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-not-null"></a><a name="general_is_not_null"></a> Nie ma wartości null
Sprawdź, czy wskaźnik nie ma wartości NULL

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-true"></a><a name="general_is_True"></a> Ma wartość true
Sprawdź, czy warunek ma wartość true

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-false"></a><a name="general_is_false"></a> Ma wartość false
Sprawdź, czy warunek jest fałszywy

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="fail"></a><a name="general_Fail"></a> Udało
Wymuś niepowodzenie wyniku przypadku testowego

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="windows-runtime-asserts"></a><a name="winrt_asserts"></a> Potwierdzenia środowisko wykonawcze systemu Windows

#### <a name="are-equal"></a><a name="winrt_are_equal"></a> Jest równe
Sprawdza, czy dwa środowisko wykonawcze systemu Windows wskaźniki są równe.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

Sprawdza, czy dwa ciągi platform:: String ^ są równe.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-same"></a><a name="winrt_are_same"></a> Są takie same
Sprawdza, czy dwie środowisko wykonawcze systemu Windows odwołują się do tego samego obiektu.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-equal"></a><a name="winrt_are_not_equal"></a> Nie są równe
Sprawdza, czy dwa środowisko wykonawcze systemu Windows wskaźniki nie są równe.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

Sprawdza, czy dwa ciągi platform:: String ^ nie są równe.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-same"></a><a name="winrt_are_not_same"></a> Nie są takie same
Sprawdza, czy dwa odwołania środowisko wykonawcze systemu Windows nie odwołują się do tego samego obiektu.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-null"></a><a name="winrt_is_null"></a> Ma wartość null
Sprawdza, czy środowisko wykonawcze systemu Windows wskaźnik jest nullptr.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-not-null"></a><a name="winrt_is_not_null"></a> Nie ma wartości null
Sprawdza, czy środowisko wykonawcze systemu Windows wskaźnik nie jest elementem nullptr.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception-asserts"></a><a name="exception_asserts"></a> Potwierdzenia wyjątków

#### <a name="expect-exception"></a><a name="expect_exception"></a> Oczekiwanie wyjątku
Sprawdź, czy funkcja zgłasza wyjątek:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

Sprawdź, czy funkcja zgłasza wyjątek:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="cppunittestloggerh"></a><a name="cppunittestlogger_h"></a> CppUnitTestLogger. h

### <a name="logger"></a><a name="logger"></a> Rejestratora
Klasa rejestratora zawiera statyczne metody do zapisu w **okno dane wyjściowe**.

### <a name="write-message"></a><a name="write_message"></a> Napisz wiadomość
Napisz ciąg do **okno dane wyjściowe**

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a><a name="example"></a> Przyklad
Ten kod jest przykładem użycia VSCppUnit. Zawiera przykłady metadanych atrybutów, armatury, testy jednostkowe z potwierdzeniami i rejestrowanie niestandardowe.

```cpp
// USAGE EXAMPLE

#include <CppUnitTest.h>

using namespace Microsoft::VisualStudio::CppUnitTestFramework;

BEGIN_TEST_MODULE_ATTRIBUTE()
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")
END_TEST_MODULE_ATTRIBUTE()

TEST_MODULE_INITIALIZE(ModuleInitialize)
{
    Logger::WriteMessage("In Module Initialize");
}

TEST_MODULE_CLEANUP(ModuleCleanup)
{
    Logger::WriteMessage("In Module Cleanup");
}

TEST_CLASS(Class1)
{

public:

    Class1()
    {
        Logger::WriteMessage("In Class1");
    }

    ~Class1()
    {
        Logger::WriteMessage("In ~Class1");
    }

    TEST_CLASS_INITIALIZE(ClassInitialize)
    {
        Logger::WriteMessage("In Class Initialize");
    }

    TEST_CLASS_CLEANUP(ClassCleanup)
    {
        Logger::WriteMessage("In Class Cleanup");
    }

    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)
        TEST_OWNER(L"OwnerName")
        TEST_PRIORITY(1)
    END_TEST_METHOD_ATTRIBUTE()

    TEST_METHOD(Method1)
    {
        Logger::WriteMessage("In Method1");
        Assert::AreEqual(0, 0);
    }

    TEST_METHOD(Method2)
    {
        Assert::Fail(L"Fail");
    }
};
```

## <a name="see-also"></a>Zobacz też

- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)
- [Zapisz testy jednostkowe dla C/C++](writing-unit-tests-for-c-cpp.md)
