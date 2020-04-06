---
title: Rejestrowanie usługi języka starszego1 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91776382fff1818986049558c9d86e8fce4d0dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705903"
---
# <a name="registering-a-legacy-language-service"></a>Rejestrowanie starszej wersji usługi językowej
W ramach pakietu zarządzanego (MPF) usługa języka jest oferowana przez vsPackage (zobacz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [VSPackages)](../../extensibility/internals/vspackages.md)i jest rejestrowana przez dodanie kluczy rejestru i wpisów. Ten proces rejestracji odbywa się częściowo podczas instalacji, a częściowo w czasie wykonywania.

## <a name="register-the-language-service-by-using-attributes"></a>Rejestrowanie usługi językowej przy użyciu atrybutów
 Następujące atrybuty są używane do rejestrowania usługi języka.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  Atrybuty te zostały wyjaśnione poniżej

### <a name="provideserviceattribute"></a>Atrybut ProvideServiceAttribute
 Ten atrybut rejestruje usługę języka jako usługę.

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

### <a name="providelanguageserviceattribute"></a>Atrybut ProvideLanguageServiceAttribute
 Ten atrybut rejestruje usługę języka specjalnie jako usługę języka. Umożliwia ustawienie opcji określających funkcje, które oferuje usługa językowa. W przykładzie przedstawiono podzbiór opcji, które usługa języka może zapewnić. Pełny zestaw opcji usług językowych <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>można znaleźć w części .

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
 Ten atrybut kojarzy usługę językową z rozszerzeniem pliku. Za każdym razem, gdy plik z tym rozszerzeniem jest ładowany, w dowolnym projekcie usługa języka jest uruchamiana i używana do wyświetlania zawartości pliku.

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
 Ten atrybut rejestruje lokalizację, z której uzyskuje się szablony rozszerzenia kodu lub fragmentu kodu. Te informacje są używane przez **przeglądarkę urywków kodu** i przez edytor, gdy fragment kodu jest wstawiany do pliku źródłowego.

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
 Ten atrybut rejestruje stronę właściwości, która ma być wyświetlana w oknie dialogowym **Opcje** w kategorii **Edytor tekstu.** Użyj jednego z tych atrybutów dla każdej strony, która ma być wyświetlana dla usługi językowej. Jeśli chcesz zorganizować strony w strukturze drzewa, użyj dodatkowych atrybutów, aby zdefiniować każdy węzeł drzewa.

### <a name="example"></a>Przykład
 W tym przykładzie przedstawiono dwie strony właściwości, **Opcje** i **Wcięcie**oraz jeden węzeł zawierający drugą stronę właściwości.

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

## <a name="proffer-the-language-service-at-run-time"></a>Proffer usługi językowej w czasie wykonywania
 Po załadowaniu pakietu językowego [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] należy poinformować, że usługa języka jest gotowa. Można to zrobić, proferując usługę. Odbywa się to <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> w metodzie. Ponadto należy uruchomić czasomierz, który wywołuje usługę języka w okresach bezczynnych, dzięki czemu można przeprowadzić analizowanie w tle. Ten czasomierz bezczynny jest również używany do aktualizowania właściwości <xref:Microsoft.VisualStudio.Package.DocumentProperties> dokumentu, jeśli zostały zaimplementowane za pośrednictwem klasy. Aby obsługiwać czasomierz, pakiet musi <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> implementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> interfejs (tylko metoda musi być w pełni zaimplementowana; pozostałe metody mogą zwracać wartości domyślne).

### <a name="example"></a>Przykład
 W tym przykładzie pokazano typowe podejście do proffering usługi i dostarczanie czasomierz bezczynny.

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
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal |
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
