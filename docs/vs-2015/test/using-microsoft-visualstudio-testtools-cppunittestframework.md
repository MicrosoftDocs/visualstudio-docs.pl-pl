---
title: Korzystanie z Microsoft. VisualStudio. TestTools. CppUnitTestFramework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c561555df40bc02c3c9f3090ee1de4c0f329bcdc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657176"
---
# <a name="using-microsoftvisualstudiotesttoolscppunittestframework"></a>Korzystanie z Microsoft.VisualStudio.TestTools.CppUnitTestFramework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie wymieniono publiczne elementy członkowskie przestrzeni nazw `Microsoft::VisualStudio::CppUnitTestFramework`.

 Pliki nagłówkowe znajdują się w folderze _VisualStudio2012 [x86] InstallFolder_ **\VC\UnitTest\include** .

 Pliki lib znajdują się w folderze _VisualStudio2012 [x86] InstallFolder_ **\VC\UnitTest\lib** .

## <a name="BKMK_In_this_topic"></a>W tym temacie
 [CppUnitTest. h](#BKMK_CppUnitTest_h)

- [Tworzenie klas i metod testowych](#BKMK_Create_test_classes_and_methods)

- [Inicjuj i oczyść](#BKMK_Initialize_and_cleanup)

  - [Metody testowe](#BKMK_Test_methods)

  - [Klasy testowe](#BKMK_Test_classes)

  - [Moduły testowe](#BKMK_Test_modules)

- [Utwórz atrybuty testu](#BKMK_Create_test_attributes)

  - [Atrybuty metody testowej](#BKMK_Test_method_attributes)

  - [Atrybuty klasy testowej](#BKMK_Test_class_attributes)

  - [Atrybuty modułu testowego](#BKMK_Test_module_attributes)

  - [Wstępnie zdefiniowane atrybuty](#BKMK_Pre_defined_attributes)

    [CppUnitTestAssert. h](#BKMK_CppUnitTestAssert_h)

  - [Potwierdzenia ogólne](#BKMK_General_Asserts)

    - [Jest równe](#BKMK_General_Are_Equal)

    - [Nie są równe](#BKMK_General_Are_Not_Equal)

    - [Są takie same](#BKMK_General_Are_Same)

    - [Nie są takie same](#BKMK_General_Are_Not_Same)

    - [Ma wartość null](#BKMK_General_Is_Null)

    - [Nie ma wartości null](#BKMK_General_Is_Not_Null)

    - [Ma wartość true](#BKMK_General_Is_True)

    - [Ma wartość false](#BKMK_General_Is_False)

    - [Udało](#BKMK_General_Fail)

  - [Potwierdzenia środowisko wykonawcze systemu Windows](#BKMK_WinRT_Asserts)

    - [Jest równe](#BKMK_WinRT_Are_Equal)

    - [Są takie same](#BKMK_WinRT_Are_Same)

    - [Nie są równe](#BKMK_WinRT_Are_Not_Equal)

    - [Nie są takie same](#BKMK_WinRT_Are_Not_Same)

    - [Ma wartość null](#BKMK_WinRT_Is_Null)

    - [Nie ma wartości null](#BKMK_WinRT_Is_Not_Null)

  - [Potwierdzenia wyjątków](#BKMK_Exception_Asserts)

    - [Oczekiwanie wyjątku](#BKMK_Expect_Exception)

      [CppUnitTestLogger. h](#BKMK_CppUnitTestLogger_h)

    - [Rejestratora](#BKMK_Logger)

    - [Napisz wiadomość](#BKMK_Write_Message)

## <a name="BKMK_CppUnitTest_h"></a>CppUnitTest. h

### <a name="BKMK_Create_test_classes_and_methods"></a>Tworzenie klas i metod testowych

```cpp
TEST_CLASS(className)
```

 Wymagane dla każdej klasy zawierającej metody testowe. Identyfikuje element *ClassName* jako klasę testową. `TEST_CLASS` musi być zadeklarowana w zakresie namescape.

```cpp
TEST_METHOD(methodName)
{
    // test method body
}

```

 Definiuje *MethodName* jako metodę testową. `TEST_METHOD` musi być zadeklarowana w zakresie klasy metody.

### <a name="BKMK_Initialize_and_cleanup"></a>Inicjuj i oczyść

#### <a name="BKMK_Test_methods"></a>Metody testowe

```cpp
TEST_METHOD_INITIALIZE(methodName)
{
    // method initialization code
}

```

 Definiuje *MethodName* jako metodę, która jest uruchamiana przed uruchomieniem każdej metody testowej. `TEST_METHOD_INITIALIZE` można zdefiniować tylko raz w klasie testowej i musi być zdefiniowana w klasie testowej.

```cpp
TEST_METHOD_CLEANUP(methodName)
{
    // test method cleanup  code
}

```

 Definiuje *MethodName* jako metodę, która jest uruchamiana po wykonaniu każdej metody testowej. `TEST_METHOD_CLEANUP` można zdefiniować tylko raz w klasie testowej i musi być zdefiniowana w zakresie klasy testowej.

#### <a name="BKMK_Test_classes"></a>Klasy testowe

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}

```

 Definiuje *MethodName* jako metodę, która jest uruchamiana po utworzeniu każdej klasy testowej. `TEST_CLASS_INITIALIZE` można zdefiniować tylko raz w klasie testowej i musi być zdefiniowana w zakresie klasy testowej.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}

```

 Definiuje *MethodName* jako metodę, która jest uruchamiana po utworzeniu każdej klasy testowej. `TEST_CLASS_CLEANUP` można zdefiniować tylko raz w klasie testowej i musi być zdefiniowana w zakresie klasy testowej.

#### <a name="BKMK_Test_modules"></a>Moduły testowe

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

### <a name="BKMK_Create_test_attributes"></a>Utwórz atrybuty testu

#### <a name="BKMK_Test_method_attributes"></a>Atrybuty metody testowej

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

 Dodaje atrybuty zdefiniowane przy użyciu co najmniej jednego makra `TEST_METHOD_ATTRIBUTE` do metody testowej *testClassName*.

 Makro `TEST_METHOD_ATTRIBUTE` definiuje atrybut o nazwie *AttributeName* i wartości *atrybutu AttributeValue*.

#### <a name="BKMK_Test_class_attributes"></a>Atrybuty klasy testowej

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

 Dodaje atrybuty zdefiniowane przy użyciu co najmniej jednego makra `TEST_CLASS_ATTRIBUTE` do klasy testowej *testClassName*.

 Makro `TEST_CLASS_ATTRIBUTE` definiuje atrybut o nazwie *AttributeName* i wartości *atrybutu AttributeValue*.

#### <a name="BKMK_Test_module_attributes"></a>Atrybuty modułu testowego

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

 Dodaje atrybuty zdefiniowane za pomocą co najmniej jednego makra `TEST_MODULE_ATTRIBUTE` do modułu testowego *testModuleName*.

 Makro `TEST_MODULE_ATTRIBUTE` definiuje atrybut o nazwie *AttributeName* i wartości *atrybutu AttributeValue*.

#### <a name="BKMK_Pre_defined_attributes"></a>Wstępnie zdefiniowane atrybuty
 Te wstępnie zdefiniowane makra atrybutów można zastąpić makra `TEST_METHOD_ATTRIBUTE`, `TEST_CLASS_ATTRIBUTE` lub `TEST_MODULE_ATTRIBUTE` opisane powyżej.

```cpp
TEST_OWNER(ownerAlias)
```

 Definiuje atrybut o nazwie `Owner` i wartości atrybutu *ownerAlias*.

```cpp
TEST_DESCRIPTION(description)
```

 Definiuje atrybut o nazwie `Description` i wartości atrybutu *Description*.

```cpp
TEST_PRIORITY(priority)
```

 Definiuje atrybut o nazwie `Priority` i wartości atrybutu *priorytet*.

```cpp
TEST_WORKITEM(workitem)
```

 Definiuje atrybut o nazwie `WorkItem` i wartości atrybutu elementu *roboczego*.

```cpp
TEST_IGNORE()
```

 Definiuje atrybut o nazwie `Ignore` i wartości atrybutu `true`.

## <a name="BKMK_CppUnitTestAssert_h"></a>CppUnitTestAssert. h

### <a name="BKMK_General_Asserts"></a>Potwierdzenia ogólne

#### <a name="BKMK_General_Are_Equal"></a>Jest równe
 Sprawdź, czy dwa obiekty są równe

```cpp
template<typename T>
static void AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa podwojone są równe

```cpp
static void AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa wartości zmiennoprzecinkowe są równe

```cpp
static void AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa znaki * są równe

```cpp
static void AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa ciągi w_char * są równe

```cpp
static void AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Are_Not_Equal"></a>Nie są równe
 Sprawdź, czy dwa podwójnej precyzji nie są równe

```cpp
static void AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa wartości zmiennoprzecinkowe nie są równe

```cpp
static void AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa znaki * nie są równe

```cpp
static void AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa ciągi w_char * nie są równe

```cpp
static void AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 Sprawdź, czy dwa odwołania nie są równe na podstawie operatora = =.

```cpp
template<typename T>
static void AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Are_Same"></a>Są takie same
 Sprawdź, czy dwa odwołania odwołują się do tego samego wystąpienia obiektu (tożsamości).

```cpp
template<typename T>
static void AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Are_Not_Same"></a>Nie są takie same
 Sprawdź, czy dwa odwołania nie odwołują się do tego samego wystąpienia obiektu (tożsamości).

```cpp
template<typename T>
static void AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Is_Null"></a>Ma wartość null
 Sprawdź, czy wskaźnik ma wartość NULL.

```cpp
template<typename T>
static void IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Is_Not_Null"></a>Nie ma wartości null
 Sprawdź, czy wskaźnik nie ma wartości NULL

```cpp
template<typename T>
static void IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Is_True"></a>Ma wartość true
 Sprawdź, czy warunek ma wartość true

```cpp
static void IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Is_False"></a>Ma wartość false
 Sprawdź, czy warunek jest fałszywy

```cpp
static void IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

#### <a name="BKMK_General_Fail"></a>Udało
 Wymuś niepowodzenie wyniku przypadku testowego

```cpp
static void Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

### <a name="BKMK_WinRT_Asserts"></a>Potwierdzenia środowisko wykonawcze systemu Windows

#### <a name="BKMK_WinRT_Are_Equal"></a>Jest równe
 Sprawdza, czy dwa środowisko wykonawcze systemu Windows wskaźniki są równe.

```
template<typename T>
static void AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Sprawdza, czy dwa ciągi platform:: String ^ są równe.

```
template<typename T>
static void AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Are_Same"></a>Są takie same
 Sprawdza, czy dwie środowisko wykonawcze systemu Windows odwołują się do tego samego obiektu.

```
template<typename T>
static void AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Are_Not_Equal"></a>Nie są równe
 Sprawdza, czy dwa środowisko wykonawcze systemu Windows wskaźniki nie są równe.

```
template<typename T>
static void AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Sprawdza, czy dwa ciągi platform:: String ^ nie są równe.

```
static void AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Are_Not_Same"></a>Nie są takie same
 Sprawdza, czy dwa odwołania środowisko wykonawcze systemu Windows nie odwołują się do tego samego obiektu.

```
template<typename T>
static void AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Is_Null"></a>Ma wartość null
 Sprawdza, czy środowisko wykonawcze systemu Windows wskaźnik jest nullptr.

```
template<typename T>
static void IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

#### <a name="BKMK_WinRT_Is_Not_Null"></a>Nie ma wartości null
 Sprawdza, czy środowisko wykonawcze systemu Windows wskaźnik nie jest elementem nullptr.

```
template<typename T>
static void IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

### <a name="BKMK_Exception_Asserts"></a>Potwierdzenia wyjątków

#### <a name="BKMK_Expect_Exception"></a>Oczekiwanie wyjątku
 Sprawdź, czy funkcja zgłasza wyjątek:

```
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

 Sprawdź, czy funkcja zgłasza wyjątek:

```
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

## <a name="BKMK_CppUnitTestLogger_h"></a>CppUnitTestLogger. h

### <a name="BKMK_Logger"></a>Rejestratora
 Klasa rejestratora zawiera statyczne metody do zapisu

```
class Logger
```

### <a name="BKMK_Write_Message"></a>Napisz wiadomość

```
static void
Logger::WriteMessage(const wchar_t* message)
```

```
static void
Logger::WriteMessage(const char* message)
```

## <a name="example"></a>Przykład
 Ten kod jest przykładem

```
////////////////////////////////////////////////////////////
/* USAGE EXAMPLE
// The following is an example of VSCppUnit usage.
// It includes examples of attribute metadata, fixtures,
// unit tests with assertions, and custom logging.

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
 [Testowanie jednostkowe](../test/unit-test-your-code.md) [kodu natywnego testów jednostkowych za pomocą Eksploratora testów](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c) [Dodawanie testów jednostkowych do istniejących C++ aplikacji](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)
