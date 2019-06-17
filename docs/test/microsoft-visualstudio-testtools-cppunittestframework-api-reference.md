---
title: Microsoft.VisualStudio.TestTools.CppUnitTestFramework API
ms.date: 06/13/2019
ms.topic: reference
ms.author: mblome
manager: jillfra
ms.workload:
- multiple
author: mikeblome
ms.openlocfilehash: 3634dcd7cf136aa52de3ebf6bf5bfc3d57632d2c
ms.sourcegitcommit: ab06cde69d862440b4277bcd9bf02e7b50593a1b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67132141"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Microsoft.VisualStudio.TestTools.CppUnitTestFramework API reference

W tym temacie wymieniono publiczne elementy członkowskie `Microsoft::VisualStudio::CppUnitTestFramework` przestrzeni nazw. Użyj tych interfejsów API do pisania testów jednostkowych C++ w oparciu o struktury testów jednostkowych natywnego firmy Microsoft. Brak [przykład użycia](#example) na końcu tego tematu.

 Pliki nagłówkowe znajdują się w _InstallFolder VisualStudio2012 [x 86]_ **\VC\UnitTest\include** folderu.

 Pliki lib znajdują się w _InstallFolder VisualStudio2012 [x 86]_ **\VC\UnitTest\lib** folderu.

Nagłówek i lib ścieżki są konfigurowane automatycznie w projekcie testowym natywnych.

## <a name="In_this_topic"></a> W tym temacie

[CppUnitTest.h](#cppUnitTest_h)

- [Tworzenie klasy testów i metody](#create_test_classes_and_methods)

- [Inicjowanie i oczyszczanie](#Initialize_and_cleanup)

  - [Metody testowe](#test_methods)

  - [Klas testowych](#test_classes)

  - [Testowanie modułów](#test_modules)

- [Utwórz atrybuty testu](#create_test_attributes)

  - [Atrybuty metody testu](#test_method_attributes)

  - [Atrybuty klasy testu](#test_class_attributes)

  - [Atrybuty modułów testu](#test_module_attributes)

  - [Wstępnie zdefiniowanych atrybutów](#pre_defined_attributes)

    [CppUnitTestAssert.h](#cppUnitTestAssert_h)

  - [Potwierdza ogólne](#general_asserts)

    - [Są takie same](#general_are_equal)

    - [Nie są takie same](#general_are_not_equal)

    - [Są takie Same](#general_are_same)

    - [Nie są takie Same](#general_are_not_same)

    - [Ma wartość Null](#general_is_null)

    - [Nie ma wartości Null](#general_is_not_null)

    - [Ma wartość True](#general_is_True)

    - [Ma wartość False](#general_is_false)

    - [Niepowodzenie](#general_Fail)

  - [Potwierdza Windows Runtime](#winrt_asserts)

    - [Są takie same](#winrt_are_equal)

    - [Są takie Same](#winrt_are_same)

    - [Nie są takie same](#winrt_are_not_equal)

    - [Nie są takie Same](#winrt_are_not_same)

    - [Ma wartość Null](#winrt_is_null)

    - [Nie ma wartości Null](#winrt_is_not_null)

  - [Wyjątek asercji](#exception_asserts)

    - [Oczekiwany wyjątek](#expect_exception)

      [CppUnitTestLogger.h](#cppunittestlogger_h)

    - [Logger](#logger)

    - [Napisz wiadomość](#write_message)

  - [Przykład użycia](#example)

## <a name="cppUnitTest_h"></a> CppUnitTest.h

### <a name="create_test_classes_and_methods"></a> Tworzenie klasy testów i metody

```cpp
TEST_CLASS(className)
```

 Wymagane dla każdej klasy zawierające metody testowe. Identyfikuje *className* jako klasy testowej. `TEST_CLASS` musi być zadeklarowana w zakresie namescape.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}
```

 Definiuje *methodName* jako metoda testowa. `TEST_METHOD` musi być zadeklarowana w zakresie metody klasy.

### <a name="Initialize_and_cleanup"></a> Inicjowanie i oczyszczanie

#### <a name="test_methods"></a> Metody testowe

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}
```

 Definiuje *methodName* jako metodę, która jest uruchamiana przed uruchomieniem każdej metody testowej. `TEST_METHOD_INITIALIZE` mogą być definiowane tylko raz w klasie testu i musi być zdefiniowany w klasie testu.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}
```

 Definiuje *methodName* jako metodę, która jest uruchamiana po uruchomieniu każdej metody testowej. `TEST_METHOD_CLEANUP` mogą być definiowane tylko raz w klasie testu i musi być zdefiniowany w zakresie klasy testowej.

#### <a name="test_classes"></a> Klas testowych

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

 Definiuje *methodName* jako metodę, która jest uruchamiana przed utworzeniem każdej klasy testowej. `TEST_CLASS_INITIALIZE` mogą być definiowane tylko raz w klasie testu i musi być zdefiniowany w zakresie klasy testowej.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

 Definiuje *methodName* jako metodę, która jest uruchamiana po utworzeniu każdej klasy testowej. `TEST_CLASS_CLEANUP` mogą być definiowane tylko raz w klasie testu i musi być zdefiniowany w zakresie klasy testowej.

#### <a name="test_modules"></a> Testowanie modułów

```cpp
TEST_MODULE_INITIALIZE(methodName)
{
    // module initialization code
}
```

 Definiuje metodę *methodName* , które jest uruchamiane po załadowaniu modułu. `TEST_MODULE_INITIALIZE` może zostać zdefiniowany tylko jeden raz w module testu i musi być zadeklarowana w zakresie przestrzeni nazw.

```cpp
TEST_MODULE_CLEANUP(methodName)
```

 Definiuje metodę *methodName* który jest uruchamiany, gdy moduł jest zwalniana. `TEST_MODULE_CLEANUP` może zostać zdefiniowany tylko jeden raz w module testu i musi być zadeklarowana w zakresie przestrzeni nazw.

### <a name="create_test_attributes"></a> Utwórz atrybuty testu

#### <a name="test_method_attributes"></a> Atrybuty metody testu

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

 Dodaje atrybuty zdefiniowane przy użyciu co najmniej jeden `TEST_METHOD_ATTRIBUTE` makra do metody testowej *testMethodName*.

 A `TEST_METHOD_ATTRIBUTE` — makro definiuje atrybut o nazwie *attributeName* i wartość *wartość atrybutu attributeValue*.

#### <a name="test_class_attributes"></a> Atrybuty klasy testu

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

 Dodaje atrybuty zdefiniowane przy użyciu co najmniej jeden `TEST_CLASS_ATTRIBUTE` makra klasy testowej *testClassName*.

 A `TEST_CLASS_ATTRIBUTE` — makro definiuje atrybut o nazwie *attributeName* i wartość *wartość atrybutu attributeValue*.

#### <a name="test_module_attributes"></a> Atrybuty modułów testu

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

 Dodaje atrybuty zdefiniowane przy użyciu co najmniej jeden `TEST_MODULE_ATTRIBUTE` makra do modułu test *testModuleName*.

 A `TEST_MODULE_ATTRIBUTE` — makro definiuje atrybut o nazwie *attributeName* i wartość *wartość atrybutu attributeValue*.

#### <a name="pre_defined_attributes"></a> Wstępnie zdefiniowanych atrybutów

 Te makra wstępnie zdefiniowanych atrybutów są dostarczane jako udogodnienie dla typowych przypadków. Można zastąpić makra `TEST_METHOD_ATTRIBUTE` opisanych powyżej.

```cpp
TEST_OWNER(ownerAlias)
```

 Definiuje `TEST_METHOD_ATTRIBUTE` o nazwie `Owner` i wartość atrybutu *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

 Definiuje `TEST_METHOD_ATTRIBUTE` o nazwie `Description` i wartość atrybutu *opis*.

```cpp
TEST_PRIORITY(priority)
```

 Definiuje `TEST_METHOD_ATTRIBUTE` o nazwie `Priority` i wartość atrybutu *priorytet*.

```cpp
TEST_WORKITEM(workitem)
```

 Definiuje `TEST_METHOD_ATTRIBUTE` o nazwie `WorkItem` i wartość atrybutu *workItem*.

```cpp
TEST_IGNORE()
```

 Definiuje `TEST_METHOD_ATTRIBUTE` o nazwie `Ignore` i wartość atrybutu `true`.

## <a name="cppUnitTestAssert_h"></a> CppUnitTestAssert.h

### <a name="general_asserts"></a> Potwierdza ogólne

#### <a name="general_are_equal"></a> Są takie same
 Sprawdź, czy dwa obiekty są równe

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwie wartości podwójnej precyzji są równe

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwie wartości zmiennoprzecinkowe są równe

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa char * ciągi są równe

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa ciągi w_char * są takie same

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_are_not_equal"></a> Nie są takie same
 Sprawdź, czy dwie wartości podwójnej precyzji nie są takie same

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwóch liczb zmiennoprzecinkowych nie są takie same

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa char * ciągi nie są równe

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa ciągi w_char * nie są równe

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa odwołania nie są równe na podstawie operatora ==.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_are_same"></a> Są takie Same
 Upewnij się, że dwa odwołania odwołują się do tego samego wystąpienia obiektu (tożsamości).

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_are_not_same"></a> Nie są takie Same
 Upewnij się, że dwa odwołania nie odwołują się do tego samego wystąpienia obiektu (tożsamości).

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_null"></a> Ma wartość Null
 Sprawdź, czy wskaźnik ma wartość NULL.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_not_null"></a> Nie ma wartości Null
 Sprawdź, czy wskaźnik nie ma wartości NULL

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_True"></a> Ma wartość True
 Sprawdź, czy warunek jest spełniony

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_is_false"></a> Ma wartość False
 Sprawdź, czy warunek jest fałszywy

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="general_Fail"></a> Niepowodzenie
 Wymuś wyniku przypadku testowego, który uległ awarii

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="winrt_asserts"></a> Potwierdza Windows Runtime

#### <a name="winrt_are_equal"></a> Są takie same
 Sprawdza, czy dwa wskaźniki środowiska uruchomieniowego Windows są takie same.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Weryfikuje, że dwa Platform::String ^ ciągi są równe.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_are_same"></a> Są takie Same
 Sprawdza, czy dwa odwołania Windows Runtime odwołują się do tego samego obiektu.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_are_not_equal"></a> Nie są takie same
 Sprawdza, czy dwa wskaźniki środowiska uruchomieniowego Windows nie są takie same.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Weryfikuje, że dwa Platform::String ^ ciągi nie są równe.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_are_not_same"></a> Nie są takie Same
 Sprawdza, czy dwa odwołania Windows Runtime nie odwołuj się do tego samego obiektu.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_is_null"></a> Ma wartość Null
 Weryfikuje, czy Windows Runtime wskaźnik nullptr.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="winrt_is_not_null"></a> Nie ma wartości Null
 Sprawdza, czy wskaźnik Windows Runtime nie jest nullptr.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="exception_asserts"></a> Wyjątek asercji

#### <a name="expect_exception"></a> Oczekiwany wyjątek
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

## <a name="cppunittestlogger_h"></a> CppUnitTestLogger.h

### <a name="logger"></a> Rejestrator
 Klasa rejestratora zawiera metody statyczne, aby zapisać **okno danych wyjściowych**.

### <a name="write_message"></a> Napisz wiadomość
Ciąg do zapisu **okno danych wyjściowych**

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a> Przykład
 Ten kod jest przykładem użycia VSCppUnit. Zawiera przykłady metadane atrybutu, uchwyty, testy jednostkowe za pomocą potwierdzenia i rejestrowania niestandardowego.

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

## <a name="see-also"></a>Zobacz także

- [Kod testu jednostkowego](../test/unit-test-your-code.md)
- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)
