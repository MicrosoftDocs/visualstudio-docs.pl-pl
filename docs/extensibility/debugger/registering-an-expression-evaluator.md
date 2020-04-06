---
title: Rejestrowanie oceniającego wyrażenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 600f7c8a2e2957cddf23ccc82b0872617e491940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713196"
---
# <a name="register-an-expression-evaluator"></a>Rejestrowanie oceniającego wyrażenia
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład oceniającego zarządzane wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Oceniający wyrażenie (EE) musi zarejestrować się jako fabryka klas zarówno w środowisku Windows COM, jak i w programie Visual Studio. EE jest skonfigurowany jako biblioteka DLL, tak aby jest wstrzykiwany do przestrzeni adresowej aparatu debugowania (DE) lub przestrzeni adresowej programu Visual Studio, w zależności od tego, która jednostka wystąpienia EE.

## <a name="managed-code-expression-evaluator"></a>Oceniający wyrażenie kodu zarządzanego
 Kod zarządzany EE jest implementowany jako biblioteka klas, która jest biblioteką DLL, która rejestruje się w środowisku COM, zwykle uruchamiana przez wywołanie programu VSIP, *regpkg.exe*. Rzeczywisty proces zapisywania kluczy rejestru dla środowiska COM jest obsługiwany automatycznie.

 Metoda klasy głównej jest oznaczona <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, wskazując, że metoda ma być wywoływana, gdy biblioteka DLL jest zarejestrowana w COM. Ta metoda rejestracji, `RegisterClass`często wywoływana, wykonuje zadanie rejestrowania biblioteki DLL w programie Visual Studio. Odpowiedni `UnregisterClass` (oznaczony <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>symbolem ), cofa skutki `RegisterClass` odinstalowania biblioteki DLL.
Te same wpisy rejestru są dokonywane jak w przypadku EE napisanego w kodzie niezarządzanym; jedyną różnicą jest to, że `SetEEMetric` nie ma funkcji pomocnika, takich jak do pracy dla Ciebie. Poniżej znajduje się przykład procesu rejestracji i wyrejestrowania.

### <a name="example"></a>Przykład
 Poniższa funkcja pokazuje, jak kod zarządzany EE rejestruje i wyrejestruje się za pomocą programu Visual Studio.

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

## <a name="unmanaged-code-expression-evaluator"></a>Ewaluator wyrażenia kodu niezarządzanego
 Biblioteka DLL EE `DllRegisterServer` implementuje funkcję, aby zarejestrować się w środowisku COM, a także visual studio.

> [!NOTE]
> Przykładowy kod mycee można znaleźć w pliku *dllentry.cpp*, który znajduje się w instalacji VSIP w obszarze EnVSDK\MyCPkgs\MyCEE.

### <a name="dll-server-process"></a>Proces serwera DLL
 Podczas rejestrowania EE serwer DLL:

1. Rejestruje swoją fabrykę `CLSID` klas zgodnie z normalnymi konwencjami COM.

2. Wywołuje funkcję `SetEEMetric` pomocnika, aby zarejestrować się w programie Visual Studio metryki EE pokazane w poniższej tabeli. Funkcja `SetEEMetric` i metryki określone w następujący sposób są częścią biblioteki *dbgmetric.lib.* Zobacz [pomocników SDK do debugowania, aby](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) uzyskać szczegółowe informacje.

    |Metryka|Opis|
    |------------|-----------------|
    |`metricCLSID`|`CLSID`fabryki klasy EE|
    |`metricName`|Nazwa EE jako ciąg wyświetlania|
    |`metricLanguage`|Nazwa języka, który EE jest przeznaczony do oceny|
    |`metricEngine`|`GUID`silników debugowania (DE), które współpracują z tym EE|

    > [!NOTE]
    > Identyfikuje `metricLanguage``GUID` język według nazwy, ale jest `guidLang` to `SetEEMetric` argument, który wybiera język. Gdy kompilator generuje plik informacji debugowania, `guidLang` należy napisać odpowiednie, tak aby DE wie, które EE do użycia. DE zazwyczaj prosi dostawcę symbolu `GUID`dla tego języka, który jest przechowywany w pliku informacji debugowania.

3. Rejestruje się w programie Visual Studio, tworząc klucze w obszarze\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*X.Y*, gdzie *X.Y* jest wersją programu Visual Studio do zarejestrowania.

### <a name="example"></a>Przykład
 Poniższa funkcja pokazuje, jak kod niezarządzany (C++) EE rejestruje i wyrejestruje się za pomocą programu Visual Studio.

```cpp
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
- [Pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Pomocnicy SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
