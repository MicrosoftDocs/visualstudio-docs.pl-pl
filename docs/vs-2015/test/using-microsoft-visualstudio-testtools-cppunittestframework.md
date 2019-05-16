---
title: Using Microsoft.VisualStudio.TestTools.CppUnitTestFramework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 10
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 77bf44460bf9670cc53703fbf3b4836016135999
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705873"
---
# <a name="using-microsoftvisualstudiotesttoolscppunittestframework"></a>Korzystanie z Microsoft.VisualStudio.TestTools.CppUnitTestFramework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie wymieniono publiczne elementy członkowskie `Microsoft::VisualStudio::CppUnitTestFramework` przestrzeni nazw.  
  
 Pliki nagłówkowe znajdują się w _InstallFolder VisualStudio2012 [x 86]_**\VC\UnitTest\include** folderu.  
  
 Pliki lib znajdują się w _InstallFolder VisualStudio2012 [x 86]_**\VC\UnitTest\lib** folderu.  
  
## <a name="BKMK_In_this_topic"></a> W tym temacie  
 [CppUnitTest.h](#BKMK_CppUnitTest_h)  
  
- [Tworzenie klasy testów i metody](#BKMK_Create_test_classes_and_methods)  
  
- [Inicjowanie i oczyszczanie](#BKMK_Initialize_and_cleanup)  
  
  - [Metody testowe](#BKMK_Test_methods)  
  
  - [Klas testowych](#BKMK_Test_classes)  
  
  - [Testowanie modułów](#BKMK_Test_modules)  
  
- [Utwórz atrybuty testu](#BKMK_Create_test_attributes)  
  
  - [Atrybuty metody testu](#BKMK_Test_method_attributes)  
  
  - [Atrybuty klasy testu](#BKMK_Test_class_attributes)  
  
  - [Atrybuty modułów testu](#BKMK_Test_module_attributes)  
  
  - [Wstępnie zdefiniowanych atrybutów](#BKMK_Pre_defined_attributes)  
  
    [CppUnitTestAssert.h](#BKMK_CppUnitTestAssert_h)  
  
  - [Potwierdza ogólne](#BKMK_General_Asserts)  
  
    - [Są takie same](#BKMK_General_Are_Equal)  
  
    - [Nie są takie same](#BKMK_General_Are_Not_Equal)  
  
    - [Są takie Same](#BKMK_General_Are_Same)  
  
    - [Nie są takie Same](#BKMK_General_Are_Not_Same)  
  
    - [Ma wartość Null](#BKMK_General_Is_Null)  
  
    - [Nie ma wartości Null](#BKMK_General_Is_Not_Null)  
  
    - [Ma wartość True](#BKMK_General_Is_True)  
  
    - [Ma wartość False](#BKMK_General_Is_False)  
  
    - [Niepowodzenie](#BKMK_General_Fail)  
  
  - [Potwierdza Windows Runtime](#BKMK_WinRT_Asserts)  
  
    - [Są takie same](#BKMK_WinRT_Are_Equal)  
  
    - [Są takie Same](#BKMK_WinRT_Are_Same)  
  
    - [Nie są takie same](#BKMK_WinRT_Are_Not_Equal)  
  
    - [Nie są takie Same](#BKMK_WinRT_Are_Not_Same)  
  
    - [Ma wartość Null](#BKMK_WinRT_Is_Null)  
  
    - [Nie ma wartości Null](#BKMK_WinRT_Is_Not_Null)  
  
  - [Wyjątek asercji](#BKMK_Exception_Asserts)  
  
    - [Oczekiwany wyjątek](#BKMK_Expect_Exception)  
  
      [CppUnitTestLogger.h](#BKMK_CppUnitTestLogger_h)  
  
    - [Logger](#BKMK_Logger)  
  
    - [Napisz wiadomość](#BKMK_Write_Message)  
  
## <a name="BKMK_CppUnitTest_h"></a> CppUnitTest.h  
  
### <a name="BKMK_Create_test_classes_and_methods"></a> Tworzenie klasy testów i metody  
  
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
  
### <a name="BKMK_Initialize_and_cleanup"></a> Inicjowanie i oczyszczanie  
  
#### <a name="BKMK_Test_methods"></a> Metody testowe  
  
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
  
#### <a name="BKMK_Test_classes"></a> Klas testowych  
  
```cpp  
TEST_CLASS_INITIALIZE(methodName)   
{  
    // test class initialization  code  
}  
  
```  
  
 Definiuje *methodName* jako metodę, która jest uruchamiana po utworzeniu każdej klasy testowej. `TEST_CLASS_INITIALIZE` mogą być definiowane tylko raz w klasie testu i musi być zdefiniowany w zakresie klasy testowej.  
  
```cpp  
TEST_CLASS_CLEANUP(methodName)   
{  
    // test class cleanup  code  
}  
  
```  
  
 Definiuje *methodName* jako metodę, która jest uruchamiana po utworzeniu każdej klasy testowej. `TEST_CLASS_CLEANUP` mogą być definiowane tylko raz w klasie testu i musi być zdefiniowany w zakresie klasy testowej.  
  
#### <a name="BKMK_Test_modules"></a> Testowanie modułów  
  
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
  
### <a name="BKMK_Create_test_attributes"></a> Utwórz atrybuty testu  
  
#### <a name="BKMK_Test_method_attributes"></a> Atrybuty metody testu  
  
```cpp  
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)   
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_METHOD_ATTRIBUTE()  
```  
  
 Dodaje atrybuty zdefiniowane przy użyciu co najmniej jeden `TEST_METHOD_ATTRIBUTE` makra do metody testowej *testClassName*.  
  
 A `TEST_METHOD_ATTRIBUTE` — makro definiuje atrybut o nazwie *attributeName* i wartość *wartość atrybutu attributeValue*.  
  
#### <a name="BKMK_Test_class_attributes"></a> Atrybuty klasy testu  
  
```cpp  
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)   
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_CLASS_ATTRIBUTE()  
```  
  
 Dodaje atrybuty zdefiniowane przy użyciu co najmniej jeden `TEST_CLASS_ATTRIBUTE` makra klasy testowej *testClassName*.  
  
 A `TEST_CLASS_ATTRIBUTE` — makro definiuje atrybut o nazwie *attributeName* i wartość *wartość atrybutu attributeValue*.  
  
#### <a name="BKMK_Test_module_attributes"></a> Atrybuty modułów testu  
  
```cpp  
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)   
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_MODULE_ATTRIBUTE()  
```  
  
 Dodaje atrybuty zdefiniowane przy użyciu co najmniej jeden `TEST_MODULE_ATTRIBUTE` makra do modułu test *testModuleName*.  
  
 A `TEST_MODULE_ATTRIBUTE` — makro definiuje atrybut o nazwie *attributeName* i wartość *wartość atrybutu attributeValue*.  
  
#### <a name="BKMK_Pre_defined_attributes"></a> Wstępnie zdefiniowanych atrybutów  
 Makra mogą zastąpić te makra wstępnie zdefiniowanych atrybutów `TEST_METHOD_ATTRIBUTE`, `TEST_CLASS_ATTRIBUTE`, lub `TEST_MODULE_ATTRIBUTE` opisanych powyżej.  
  
```cpp  
TEST_OWNER(ownerAlias)  
```  
  
 Definiuje atrybut o nazwie `Owner` i wartość atrybutu *ownerAlias*.  
  
```cpp  
TEST_DESCRIPTION(description)  
```  
  
 Definiuje atrybut o nazwie `Description` i wartość atrybutu *opis*.  
  
```cpp  
TEST_PRIORITY(priority)  
```  
  
 Definiuje atrybut o nazwie `Priority` i wartość atrybutu *priorytet*.  
  
```cpp  
TEST_WORKITEM(workitem)  
```  
  
 Definiuje atrybut o nazwie `WorkItem` i wartość atrybutu *workItem*.  
  
```cpp  
TEST_IGNORE()  
```  
  
 Definiuje atrybut o nazwie `Ignore` i wartość atrybutu `true`.  
  
## <a name="BKMK_CppUnitTestAssert_h"></a> CppUnitTestAssert.h  
  
### <a name="BKMK_General_Asserts"></a> Potwierdza ogólne  
  
#### <a name="BKMK_General_Are_Equal"></a> Są takie same  
 Sprawdź, czy dwa obiekty są równe  
  
```cpp  
template<typename T>   
static void AreEqual(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Sprawdź, czy dwie wartości podwójnej precyzji są równe  
  
```cpp  
static void AreEqual(  
    double expected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Sprawdź, czy dwie wartości zmiennoprzecinkowe są równe  
  
```cpp  
static void AreEqual(  
    float expected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Sprawdź, czy dwa char * ciągi są równe  
  
```cpp  
static void AreEqual(  
    const char* expected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Sprawdź, czy dwa ciągi w_char * są takie same  
  
```cpp  
static void AreEqual(  
    const wchar_t* expected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Are_Not_Equal"></a> Nie są takie same  
 Sprawdź, czy dwie wartości podwójnej precyzji nie są takie same  
  
```cpp  
static void AreNotEqual(  
    double notExpected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Sprawdź, czy dwóch liczb zmiennoprzecinkowych nie są takie same  
  
```cpp  
static void AreNotEqual(  
    float notExpected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 Sprawdź, czy dwa char * ciągi nie są równe  
  
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
  
 Sprawdź, czy dwa odwołania nie są równe na podstawie operatora ==.  
  
```cpp  
template<typename T>   
static void AreNotEqual(  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Are_Same"></a> Są takie Same  
 Upewnij się, że dwa odwołania odwołują się do tego samego wystąpienia obiektu (tożsamości).  
  
```cpp  
template<typename T>   
static void AreSame(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Are_Not_Same"></a> Nie są takie Same  
 Upewnij się, że dwa odwołania nie odwołują się do tego samego wystąpienia obiektu (tożsamości).  
  
```cpp  
template<typename T>   
static void AreNotSame (  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Is_Null"></a> Ma wartość Null  
 Sprawdź, czy wskaźnik ma wartość NULL.  
  
```cpp  
template<typename T>   
static void IsNull(  
    const T* actual,  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Is_Not_Null"></a> Nie ma wartości Null  
 Sprawdź, czy wskaźnik nie ma wartości NULL  
  
```cpp  
template<typename T>   
static void IsNotNull(  
    const T* actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Is_True"></a> Ma wartość True  
 Sprawdź, czy warunek jest spełniony  
  
```cpp  
static void IsTrue(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Is_False"></a> Ma wartość False  
 Sprawdź, czy warunek jest fałszywy  
  
```cpp  
static void IsFalse(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
#### <a name="BKMK_General_Fail"></a> Niepowodzenie  
 Wymuś wyniku przypadku testowego, który uległ awarii  
  
```cpp  
static void Fail(  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
### <a name="BKMK_WinRT_Asserts"></a> Potwierdza Windows Runtime  
  
#### <a name="BKMK_WinRT_Are_Equal"></a> Są takie same  
 Sprawdza, czy dwa wskaźniki środowiska uruchomieniowego Windows są takie same.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Weryfikuje, że dwa Platform::String ^ ciągi są równe.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
#### <a name="BKMK_WinRT_Are_Same"></a> Są takie Same  
 Sprawdza, czy dwa odwołania Windows Runtime odwołują się do tego samego obiektu.  
  
```  
template<typename T>   
static void AreSame(  
    T% expected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
#### <a name="BKMK_WinRT_Are_Not_Equal"></a> Nie są takie same  
 Sprawdza, czy dwa wskaźniki środowiska uruchomieniowego Windows nie są takie same.  
  
```  
template<typename T>   
static void AreNotEqual(  
    T^ notExpected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Weryfikuje, że dwa Platform::String ^ ciągi nie są równe.  
  
```  
static void AreNotEqual(  
    Platform::String^ notExpected,   
    Platform::String^ actual,   
    bool ignoreCase = false,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
#### <a name="BKMK_WinRT_Are_Not_Same"></a> Nie są takie Same  
 Sprawdza, czy dwa odwołania Windows Runtime nie odwołuj się do tego samego obiektu.  
  
```  
template<typename T>   
static void AreNotSame(  
    T% notExpected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
#### <a name="BKMK_WinRT_Is_Null"></a> Ma wartość Null  
 Weryfikuje, czy Windows Runtime wskaźnik nullptr.  
  
```  
template<typename T>   
static void IsNull(  
    T^ actual,  
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
#### <a name="BKMK_WinRT_Is_Not_Null"></a> Nie ma wartości Null  
 Sprawdza, czy wskaźnik Windows Runtime nie jest nullptr.  
  
```  
template<typename T>   
static void IsNotNull(  
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
### <a name="BKMK_Exception_Asserts"></a> Wyjątek asercji  
  
#### <a name="BKMK_Expect_Exception"></a> Oczekiwany wyjątek  
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
  
## <a name="BKMK_CppUnitTestLogger_h"></a> CppUnitTestLogger.h  
  
### <a name="BKMK_Logger"></a> Rejestrator  
 Klasa rejestratora zawiera metody statyczne do zapisu  
  
```  
class Logger  
```  
  
### <a name="BKMK_Write_Message"></a> Napisz wiadomość  
  
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
 [Testowanie jednostek kodu](../test/unit-test-your-code.md)   
 [Testy jednostkowe kodu natywnego za pomocą narzędzia Eksplorator testów](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)   
 [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)
