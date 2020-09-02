---
title: Rejestrowanie ewaluatora wyrażeń | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3595daa51fddf5c9c027d5643382918d85f83cc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837886"
---
# <a name="registering-an-expression-evaluator"></a>Rejestrowanie ewaluatora wyrażeń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ewaluatora wyrażeń (EE) musi być zarejestrowana jako fabryka klas zarówno w środowisku Windows COM, jak i w programie Visual Studio. Program EE jest zaimplementowany jako biblioteka DLL, aby można go było wstrzyknąć do przestrzeni adresowej aparatu debugowania (DE) lub przestrzeni adresowej programu Visual Studio, w zależności od tego, który obiekt tworzy wystąpienie programu EE.  
  
## <a name="managed-code-expression-evaluator"></a>Ewaluatora wyrażeń kodu zarządzanego  
 Zarządzany kod EE jest implementowany jako Biblioteka klas, która jest biblioteką DLL, która zarejestruje się ze środowiskiem COM, zazwyczaj uruchamiana przez wywołanie **regpkg.exe**programu VSIP. Rzeczywisty proces zapisywania kluczy rejestru dla środowiska COM jest obsługiwany automatycznie.  
  
 Metoda klasy głównej jest oznaczona przy użyciu <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> , wskazując, że metoda ma być wywoływana, gdy biblioteka DLL jest zarejestrowana w modelu com. Ta metoda rejestracji, często wywoływana `RegisterClass` , wykonuje zadanie rejestrowania biblioteki DLL w programie Visual Studio. Odpowiadająca `UnregisterClass` (oznaczona znakiem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> ), powoduje, że nie ma wpływu `RegisterClass` na to, kiedy Biblioteka DLL zostanie odinstalowana.  
  
 Te same wpisy rejestru są wykonywane jak w przypadku EE pisanych w kodzie niezarządzanym. Jedyną różnicą jest to, że nie ma żadnych funkcji pomocnika, takich jak `SetEEMetric` wykonywanie pracy. Przykład tego procesu rejestracji/wyrejestrowywania wygląda następująco:  
  
### <a name="example"></a>Przykład  
 Ta funkcja pokazuje, jak zarządzany kod EE rejestruje i wyrejestrowuje się z programu Visual Studio.  
  
```csharp  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        #region Register and unregister.  
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");  
        private static string languageName = "MyC";  
        private static string eeName = "MyC Expression Evaluator";  
  
        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");  
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");  
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");  
  
        /// <summary>  
        /// Register the expression evaluator.  
        /// Set "project properties/configuration properties/build/register for COM interop" to true.  
        /// </summary>  
         [ComRegisterFunctionAttribute]  
        public static void RegisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator";  
  
            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);  
            if (rk == null)  return;  
  
            rk = rk.CreateSubKey(guidMycLang.ToString("B"));  
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));  
            rk.SetValue("CLSID", t.GUID.ToString("B"));  
            rk.SetValue("Language", languageName);  
            rk.SetValue("Name", eeName);  
  
            rk = rk.CreateSubKey("Engine");  
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));  
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));  
        }  
        /// <summary>  
        /// Unregister the expression evaluator.  
        /// </summary>  
         [ComUnregisterFunctionAttribute]  
        public static void UnregisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator\"  
                        + guidMycLang.ToString("B");  
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);  
            if (key != null)  
            {  
                key.Close();  
                Registry.LocalMachine.DeleteSubKeyTree(s);  
            }  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code-expression-evaluator"></a>Ewaluatora wyrażeń kodu niezarządzanego  
 Biblioteka DLL EE implementuje `DllRegisterServer` funkcję w celu zarejestrowania się w środowisku com, a także w programie Visual Studio.  
  
> [!NOTE]
> Kod rejestru przykładowego kodu MyCEE można znaleźć w pliku dllentry. cpp, który znajduje się w instalacji VSIP w obszarze EnVSDK\MyCPkgs\MyCEE.  
  
### <a name="dll-server-process"></a>Proces serwera DLL  
 Podczas rejestrowania programu EE serwer DLL:  
  
1. Rejestruje fabrykę klas `CLSID` zgodnie z normalnymi konwencjami com.  
  
2. Wywołuje funkcję pomocnika, `SetEEMetric` Aby zarejestrować się w programie Visual Studio metryki EE pokazane w poniższej tabeli. Funkcja `SetEEMetric` i metryki określone poniżej są częścią biblioteki dbgmetric. lib. Aby uzyskać szczegółowe informacje, zobacz [pomocników zestawu SDK](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) .  
  
    |Metryka|Opis|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` fabryki klas EE|  
    |`metricName`|Nazwa EE jako ciąg, który ma być odtwarzany|  
    |`metricLanguage`|Nazwa języka, który ma być przeznaczony do oszacowania|  
    |`metricEngine`|`GUID`s aparatów debugowania (DE), które działają w tym EE|  
  
    > [!NOTE]
    > `metricLanguage``GUID`Identyfikuje język według nazwy, ale jest `guidLang` argumentem `SetEEMetric` , który wybiera język. Po wygenerowaniu przez kompilator pliku informacji o debugowaniu należy napisać odpowiednie polecenie, aby uzyskać informacje o tym, które `guidLang` EE mają być używane. Zwykle prosi dostawcę symboli dla tego języka `GUID` , który jest przechowywany w pliku informacji o debugowaniu.  
  
3. Rejestruje w programie Visual Studio, tworząc klucze w obszarze HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *x. y*, gdzie *x. y* jest wersją programu Visual Studio do zarejestrowania.  
  
### <a name="example"></a>Przykład  
 Ta funkcja pokazuje, jak kod niezarządzany (C++) EE rejestruje się i wyrejestrowuje z programu Visual Studio.  
  
```cpp#  
/*---------------------------------------------------------  
  Registration  
-----------------------------------------------------------*/  
#ifndef LREGKEY_VISUALSTUDIOROOT  
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"  
#endif  
  
static HRESULT RegisterMetric( bool registerIt )  
{  
    // check where we should register  
    const ULONG cchBuffer = _MAX_PATH;  
    WCHAR wszRegistrationRoot[cchBuffer];  
    DWORD cchFreeBuffer = cchBuffer - 1;  
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);  
    wcscat(wszRegistrationRoot, L"\\");  
  
    // this is Environment SDK specific  
    // we check for  EnvSdk_RegKey environment variable to  
    // determine where to register  
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;  
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;  
    DWORD cchEnvVarRead = GetEnvironmentVariableW(  
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name  
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value  
        /* DWORD   */ cchFreeBuffer);// size of buffer  
    if (cchEnvVarRead >= cchFreeBuffer)  
        return E_UNEXPECTED;  
    // If the environment variable does not exist then we must use   
    // LREGKEY_VISUALSTUDIOROOT which has the version number.  
    if (0 == cchEnvVarRead)  
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);  
  
    if (registerIt)  
    {  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricCLSID,  
                    CLSID_MycEE,  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricName,  
                    GetString(IDS_INFO_MYCDESCRIPTION),  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricLanguage, L"MyC",  
                    wszRegistrationRoot);  
  
        GUID engineGuids[2];  
        engineGuids[0] = guidCOMPlusOnlyEng;  
        engineGuids[1] = guidCOMPlusNativeEng;  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricEngine,  
                    engineGuids,  
                    2,  
                    wszRegistrationRoot);  
    }  
    else  
    {  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricCLSID,  
                        wszRegistrationRoot);  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricName,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricLanguage,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricEngine,  
                        wszRegistrationRoot );  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Pomocnicy zestawu SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
