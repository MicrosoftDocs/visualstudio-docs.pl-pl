---
title: Rejestrowanie starszej wersji usługi językowej1 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d78050f455e83b43dc114ad80fc084dc5604103
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188865"
---
# <a name="registering-a-legacy-language-service"></a>Rejestrowanie starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W ramach pakietu zarządzanego (MPF), usługa języka jest proffered przez pakietu VSPackage (zobacz [pakietów VSPackage](../../extensibility/internals/vspackages.md)) i jest zarejestrowany w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] przez dodanie klucze i wpisy. Ten proces rejestracji odbywa się w częściowo podczas instalacji i częściowo w czasie wykonywania.  
  
## <a name="register-the-language-service-by-using-attributes"></a>Zarejestruj usługę języka przy użyciu atrybutów  
 Następujące atrybuty są używane do rejestrowania usługi języka.  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>  
  
  Poniżej opisano te atrybuty  
  
### <a name="provideserviceattribute"></a>ProvideServiceAttribute  
 Ten atrybut rejestruje usługi języka jako usługa.  
  
### <a name="example"></a>Przykład  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideServiceAttribute(typeof(TestLanguageService),  
                             ServiceName = "Test Language Service")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageserviceattribute"></a>ProvideLanguageServiceAttribute  
 Ten atrybut rejestruje usługi języka specjalnie jako usługa języka. Umożliwia ustawianie opcji, które określają funkcje, które oferuje usługi w języka. W przykładzie pokazano podzbiór opcje, które zapewniają usługi języka. Aby uzyskać pełny zestaw opcji usługi w języka, zobacz <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>.  
  
### <a name="example"></a>Przykład  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),  
                             "Test Language",  
                             106,             // resource ID of localized language name  
                             CodeSense = true,             // Supports IntelliSense  
                             RequestStockColors = false,   // Supplies custom colors  
                             EnableCommenting = true,      // Supports commenting out code  
                             EnableAsyncCompletion = true  // Supports background parsing  
                             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageextensionattribute"></a>ProvideLanguageExtensionAttribute  
 Ten atrybut kojarzy usługi języka z rozszerzeniem pliku. Przy każdym załadowaniu pliku z tym rozszerzeniem w każdym projekcie usługi w języka jest uruchomiona i używany do wyświetlania zawartości pliku.  
  
### <a name="example"></a>Przykład  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),  
                                       ".Testext")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguagecodeexpansionattribute"></a>ProvideLanguageCodeExpansionAttribute  
 Ten atrybut rejestruje lokalizacji, z kodu, które są uzyskiwane szablonów rozszerzeń lub wstawieniu fragmentu kodu. Te informacje są używane przez **przeglądarki fragmenty kodu** i przez Edytor po wstawieniu fragmentu kodu do pliku źródłowego.  
  
### <a name="example"></a>Przykład  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageCodeExpansionAttribute(  
             typeof(TestLanguageService),  
             "Test Language", // Name of language used as registry key.  
             106,           // Resource ID of localized name of language service.  
             "testlanguage",  // language key used in snippet templates.  
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index  
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +  
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageeditoroptionpageattribute"></a>ProvideLanguageEditorOptionPageAttribute  
 Ten atrybut rejestruje strony właściwości mają być wyświetlane w **opcje** okno dialogowe, w obszarze **edytora tekstów** kategorii. Użyj jednej z tych atrybutów dla każdej strony ma być wyświetlany dla usługi języka. Jeśli potrzebujesz do organizowania stron w strukturze drzewa, należy użyć dodatkowych atrybutów do definiowania każdego węzła drzewa.  
  
### <a name="example"></a>Przykład  
 Dwie strony właściwości, w tym przykładzie **opcje** i **Indenting**i jednego węzła, który zawiera drugiej strony właściwości.  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Options",      // Registry key name for property page  
             "#242",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Advanced",     // Registry key name for node  
             "#243",         // Localized name of node  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             @"Advanced\Indenting",     // Registry key name for property page  
             "#244",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
## <a name="proffer-the-language-service-at-runtime"></a>Udąło usługa językowa w czasie wykonywania  
 Po załadowaniu pakietu języka, musisz poinformować [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , usługa języka jest gotowy. W tym celu proffering usługi. Jest to realizowane w <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody. Ponadto należy uruchomić czasomierza, który wywołuje usługi języka w okresach bezczynności, dzięki czemu analizowanie w tle można osiągnąć. Ta czasomierza bezczynności jest również używane do aktualizacji właściwości dokumentu, jeśli udało Ci się wdrożyć dowolny za pośrednictwem <xref:Microsoft.VisualStudio.Package.DocumentProperties> klasy. Aby można było obsługiwać czasomierz, musi implementować pakietu <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> interfejsu (tylko <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> metoda musi być w pełni zaimplementowane; pozostałe metody może zwracać wartości domyślnej).  
  
### <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono typowe podejście do proffering usługi i dostarczenie czasomierza bezczynności.  
  
```csharp  
  
using System;  
using System.Runtime.InteropServices;  
using System.ComponentModel.Design;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.OLE.Interop;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,  
        AutoOutlining = true,  
        EnableCommenting = true,  
        MatchBraces = true,  
        ShowMatchingBrace = true)]  
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package  
  
    public class TestLanguagePackage : Package, IOleComponent  
    {  
        private uint m_componentID;  
  
        protected override void Initialize()  
        {  
            base.Initialize();  // required  
  
            // Proffer the service.  
            IServiceContainer serviceContainer = this as IServiceContainer;  
            TestLanguageService langService      = new TestLanguageService();  
            langService.SetSite(this);  
            serviceContainer.AddService(typeof(TestLanguageService),  
                                        langService,  
                                        true);  
  
            // Register a timer to call our language service during  
            // idle periods.  
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                       as IOleComponentManager;  
            if (m_componentID == 0 && mgr != null)  
            {  
                OLECRINFO[] crinfo = new OLECRINFO[1];  
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));  
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |  
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;  
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal     |  
                                              (uint)_OLECADVF.olecadvfRedrawOff |  
                                              (uint)_OLECADVF.olecadvfWarningsOff;  
                crinfo[0].uIdleTimeInterval = 1000;  
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);  
            }  
        }  
  
        protected override void Dispose(bool disposing)  
        {  
            if (m_componentID != 0)  
            {  
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                           as IOleComponentManager;  
                if (mgr != null)  
                {  
                    int hr = mgr.FRevokeComponent(m_componentID);  
                }  
                m_componentID = 0;  
            }  
  
            base.Dispose(disposing);  
        }  
  
        #region IOleComponent Members  
  
        public int FDoIdle(uint grfidlef)  
        {  
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;  
            // Use typeof(TestLanguageService) because we need to  
            // reference the GUID for our language service.  
            LanguageService service = GetService(typeof(TestLanguageService))  
                                      as LanguageService;  
            if (service != null)  
            {  
                service.OnIdle(bPeriodic);  
            }  
            return 0;  
        }  
  
        public int FContinueMessageLoop(uint uReason,  
                                        IntPtr pvLoopData,  
                                        MSG[] pMsgPeeked)  
        {  
            return 1;  
        }  
  
        public int FPreTranslateMessage(MSG[] pMsg)  
        {  
            return 0;  
        }  
  
        public int FQueryTerminate(int fPromptUser)  
        {  
            return 1;  
        }  
  
        public int FReserved1(uint dwReserved,  
                              uint message,  
                              IntPtr wParam,  
                              IntPtr lParam)  
        {  
            return 1;  
        }  
  
        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)  
        {  
            return IntPtr.Zero;  
        }  
  
        public void OnActivationChange(IOleComponent pic,  
                                       int fSameComponent,  
                                       OLECRINFO[] pcrinfo,  
                                       int fHostIsActivating,  
                                       OLECHOSTINFO[] pchostinfo,  
                                       uint dwReserved)  
        {  
        }  
  
        public void OnAppActivate(int fActive, uint dwOtherThreadID)  
        {  
        }  
  
        public void OnEnterState(uint uStateID, int fEnter)  
        {  
        }  
  
        public void OnLoseActivation()  
        {  
        }  
  
        public void Terminate()  
        {  
        }  
  
        #endregion  
    }  
}   
```
