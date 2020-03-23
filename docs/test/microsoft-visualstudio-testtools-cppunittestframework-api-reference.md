---
title: Microsoft.VisualStudio.TestTools.CppUnitTestFramework API
ms.date: 09/27/2019
ms.topic: reference
ms.author: corob
manager: jillfra
ms.workload:
- multiple
author: corob-msft
ms.openlocfilehash: 8a71b6d406b7507930a5d1a7ce593a296220d5a6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77278648"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Odwołanie do interfejsu API Microsoft.VisualStudio.TestTools.CppUnitTestFramework

W tym temacie wymieniono `Microsoft::VisualStudio::CppUnitTestFramework` publiczne elementy członkowskie obszaru nazw. Użyj tych interfejsów API do pisania testów jednostkowych języka C++ na podstawie struktury testów jednostek natywnych firmy Microsoft. Na końcu tematu znajduje się [przykład użycia.](#example)

Pliki nagłówka i lib znajdują się w * \<folderze instalacyjnym programu Visual Studio>\VC\Auxiliary\VS\UnitTest*.

Ścieżki nagłówka i lib są automatycznie konfigurowane w projekcie testu macierzystego.

## <a name="in-this-topic"></a><a name="In_this_topic"></a>W tym temacie

[CppUnitTest.h](#cppUnitTest_h)

- [Tworzenie klas i metod testów](#create_test_classes_and_methods)

- [Inicjowanie i oczyszczanie](#Initialize_and_cleanup)

  - [Metody badań](#test_methods)

  - [Klasy testowe](#test_classes)

  - [Moduły testowe](#test_modules)

- [Tworzenie atrybutów testu](#create_test_attributes)

  - [Atrybuty metody testowej](#test_method_attributes)

  - [Testowanie atrybutów klasy](#test_class_attributes)

  - [Atrybuty modułu testowego](#test_module_attributes)

  - [Wstępnie zdefiniowane atrybuty](#pre_defined_attributes)

    [CppUnitTestAssert.h](#cppUnitTestAssert_h)

  - [Potwierdzenia ogólne](#general_asserts)

    - [Są równe](#general_are_equal)

    - [Nie są równe](#general_are_not_equal)

    - [Są takie same](#general_are_same)

    - [Nie są takie same](#general_are_not_same)

    - [Ma wartość null](#general_is_null)

    - [Nie ma wartości null](#general_is_not_null)

    - [Jest prawdziwa](#general_is_True)

    - [Jest false](#general_is_false)

    - [Niepowodzenie](#general_Fail)

  - [Potwierdzenia środowiska wykonawczego systemu Windows](#winrt_asserts)

    - [Są równe](#winrt_are_equal)

    - [Są takie same](#winrt_are_same)

    - [Nie są równe](#winrt_are_not_equal)

    - [Nie są takie same](#winrt_are_not_same)

    - [Ma wartość null](#winrt_is_null)

    - [Nie ma wartości null](#winrt_is_not_null)

  - [Potwierdzenia wyjątków](#exception_asserts)

    - [Spodziewaj się wyjątku](#expect_exception)

      [CppUnitTestLogger.h](#cppunittestlogger_h)

    - [Rejestratora](#logger)

    - [Napisz wiadomość](#write_message)

  - [Przykład użycia](#example)

## <a name="cppunittesth"></a><a name="cppUnitTest_h"></a>CppUnitTest.h

### <a name="create-test-classes-and-methods"></a><a name="create_test_classes_and_methods"></a>Tworzenie klas i metod testów

```cpp
TEST_CLASS(className)
```

Wymagane dla każdej klasy zawierającej metody badawcze. Identyfikuje *className* jako klasę testową. `TEST_CLASS`należy zadeklarować w zakresie namescape.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

Definiuje *methodName* jako metodę testową. `TEST_METHOD`muszą być zadeklarowane w zakresie klasy metody.

### <a name="initialize-and-cleanup"></a><a name="Initialize_and_cleanup"></a>Inicjowanie i oczyszczanie

#### <a name="test-methods"></a><a name="test_methods"></a>Metody badań

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

Definiuje *methodName* jako metodę, która jest uruchamiana przed uruchomieniem każdej metody testowej. `TEST_METHOD_INITIALIZE`można zdefiniować tylko raz w klasie badania i muszą być zdefiniowane w zakresie klasy badania.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

Definiuje *methodName* jako metodę, która jest uruchamiana po uruchomieniu każdej metody testowej. `TEST_METHOD_CLEANUP`można zdefiniować tylko raz w klasie badania i muszą być zdefiniowane w zakresie klasy badania.

#### <a name="test-classes"></a><a name="test_classes"></a>Klasy testowe

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

Definiuje *methodName* jako metodę, która jest uruchamiana przed utworzeniem każdej klasy testowej. `TEST_CLASS_INITIALIZE`można zdefiniować tylko raz w klasie badania i muszą być zdefiniowane w zakresie klasy badania.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

Definiuje *methodName* jako metodę, która jest uruchamiana po każdej klasy testowej jest tworzony. `TEST_CLASS_CLEANUP`można zdefiniować tylko raz w klasie badania i muszą być zdefiniowane w zakresie klasy badania.

#### <a name="test-modules"></a><a name="test_modules"></a>Moduły testowe

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

Definiuje *metodęName,* która jest uruchamiana po załadowaniu modułu. `TEST_MODULE_INITIALIZE`można zdefiniować tylko raz w module testowym i muszą być zadeklarowane w zakresie obszaru nazw.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

Definiuje *metodęName,* która jest uruchamiana, gdy moduł jest zwalniany. `TEST_MODULE_CLEANUP`można zdefiniować tylko raz w module testowym i muszą być zadeklarowane w zakresie obszaru nazw.

### <a name="create-test-attributes"></a><a name="create_test_attributes"></a>Tworzenie atrybutów testu

#### <a name="test-method-attributes"></a><a name="test_method_attributes"></a>Atrybuty metody testowej

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

Dodaje atrybuty zdefiniowane `TEST_METHOD_ATTRIBUTE` za pomocą jednego lub więcej makr do testu metody testowejMethodName . *testMethodName*

Makro `TEST_METHOD_ATTRIBUTE` definiuje atrybut z *atrybutem nameeName* i *atrybutem valueValue*.

#### <a name="test-class-attributes"></a><a name="test_class_attributes"></a>Testowanie atrybutów klasy

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

Dodaje atrybuty zdefiniowane `TEST_CLASS_ATTRIBUTE` za pomocą jednego lub więcej makr do testu klasy testowejClassName . *testClassName*

Makro `TEST_CLASS_ATTRIBUTE` definiuje atrybut z *atrybutem nameeName* i *atrybutem valueValue*.

#### <a name="test-module-attributes"></a><a name="test_module_attributes"></a>Atrybuty modułu testowego

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

Dodaje atrybuty zdefiniowane `TEST_MODULE_ATTRIBUTE` za pomocą jednego lub więcej makr do *modułu testowegoModuleName*.

Makro `TEST_MODULE_ATTRIBUTE` definiuje atrybut z *atrybutem nameeName* i *atrybutem valueValue*.

#### <a name="pre-defined-attributes"></a><a name="pre_defined_attributes"></a>Wstępnie zdefiniowane atrybuty

Te wstępnie zdefiniowane makra atrybutów są dostarczane jako udogodnienie dla typowych przypadków. Można je zastąpić makro `TEST_METHOD_ATTRIBUTE` opisane powyżej.

```cpp
TEST_OWNER(ownerAlias)
```

Definiuje `TEST_METHOD_ATTRIBUTE` nazwę `Owner` i wartość atrybutu *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

Definiuje `TEST_METHOD_ATTRIBUTE` a z `Description` nazwą i wartością atrybutu *opisu*.

```cpp
TEST_PRIORITY(priority)
```

Definiuje `TEST_METHOD_ATTRIBUTE` nazwę `Priority` i wartość atrybutu *priorytetu*.

```cpp
TEST_WORKITEM(workitem)
```

Definiuje `TEST_METHOD_ATTRIBUTE` a z `WorkItem` nazwą i wartością atrybutu *workItem*.

```cpp
TEST_IGNORE()
```

Definiuje `TEST_METHOD_ATTRIBUTE` a z `Ignore` nazwą i wartością `true`atrybutu .

## <a name="cppunittestasserth"></a><a name="cppUnitTestAssert_h"></a>CppUnitTestAssert.h

### <a name="general-asserts"></a><a name="general_asserts"></a>Potwierdzenia ogólne

#### <a name="are-equal"></a><a name="general_are_equal"></a>Są równe
Sprawdź, czy dwa obiekty są równe

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa dublety są równe

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa pływaki są równe

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa ciągi char* są równe

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa ciągi w_char* są równe

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-equal"></a><a name="general_are_not_equal"></a>Nie są równe
Sprawdź, czy dwa dublety nie są równe

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa pływaki nie są równe

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa ciągi char* nie są równe

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa ciągi w_char* nie są równe

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

Sprawdź, czy dwa odwołania nie są równe na podstawie operator==.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-same"></a><a name="general_are_same"></a>Są takie same
Sprawdź, czy dwa odwołania odnoszą się do tego samego wystąpienia obiektu (tożsamości).

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="are-not-same"></a><a name="general_are_not_same"></a>Nie są takie same
Sprawdź, czy dwa odwołania nie odnoszą się do tego samego wystąpienia obiektu (tożsamości).

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-null"></a><a name="general_is_null"></a>Ma wartość null
Sprawdź, czy wskaźnik ma wartość NULL.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-not-null"></a><a name="general_is_not_null"></a>Nie ma wartości null
Sprawdź, czy wskaźnik nie ma wartości NULL

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-true"></a><a name="general_is_True"></a>Jest prawdziwa
Sprawdzanie, czy warunek jest spełniony

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="is-false"></a><a name="general_is_false"></a>Jest false
Sprawdź, czy warunek jest fałszywy

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="fail"></a><a name="general_Fail"></a>Nie
Wymuszanie niepowodzenia wyniku przypadku testowego

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="windows-runtime-asserts"></a><a name="winrt_asserts"></a>Potwierdzenia środowiska wykonawczego systemu Windows

#### <a name="are-equal"></a><a name="winrt_are_equal"></a>Są równe
Sprawdza, czy dwa wskaźniki środowiska wykonawczego systemu Windows są równe.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

Sprawdza, czy dwa ciągi platform::String^ są równe.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-same"></a><a name="winrt_are_same"></a>Są takie same
Sprawdza, czy dwa odwołania środowiska wykonawczego systemu Windows odwołują się do tego samego obiektu.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-equal"></a><a name="winrt_are_not_equal"></a>Nie są równe
Sprawdza, czy dwa wskaźniki środowiska wykonawczego systemu Windows nie są równe.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

Sprawdza, czy dwa ciągi platform::String^ nie są równe.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="are-not-same"></a><a name="winrt_are_not_same"></a>Nie są takie same
Sprawdza, czy dwa odwołania środowiska wykonawczego systemu Windows nie odwołują się do tego samego obiektu.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-null"></a><a name="winrt_is_null"></a>Ma wartość null
Sprawdza, czy wskaźnik środowiska wykonawczego systemu Windows jest nullptr.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="is-not-null"></a><a name="winrt_is_not_null"></a>Nie ma wartości null
Sprawdza, czy wskaźnik środowiska wykonawczego systemu Windows nie jest nullptr.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception-asserts"></a><a name="exception_asserts"></a>Potwierdzenia wyjątków

#### <a name="expect-exception"></a><a name="expect_exception"></a>Spodziewaj się wyjątku
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

## <a name="cppunittestloggerh"></a><a name="cppunittestlogger_h"></a>CppUnitTestLogger.h

### <a name="logger"></a><a name="logger"></a>Rejestratora
Klasa Logger zawiera metody statyczne do zapisu w **oknie wyjściowym**.

### <a name="write-message"></a><a name="write_message"></a>Napisz wiadomość
Zapisanie ciągu w **oknie wyjściowym**

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a><a name="example"></a>Przykład
Ten kod jest przykładem użycia VSCppUnit. Zawiera przykłady metadanych atrybutów, urządzeń, testów jednostkowych z potwierdzeniami i niestandardowych rejestrowania.

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

- [Jednostka przetestować swój kod](../test/unit-test-your-code.md)
- [Zapis testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
