---
title: Rejestrowanie starszej wersji językowej Service1 | Microsoft Docs
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
ms.openlocfilehash: f0076eeee0ebcb0a80925efdde212097a3ec3e7e
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238884"
---
# <a name="registering-a-legacy-language-service-1"></a>Rejestrowanie starszej wersji usługi językowej 1
W strukturze pakietów zarządzanych (MPF) usługa języka jest proffered przez pakietu VSPackage (zobacz [pakietów VSPackage](../../extensibility/internals/vspackages.md)) i jest zarejestrowana w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] przez dodanie kluczy rejestru i wpisów. Ten proces rejestracji odbywa się częściowo podczas instalacji i częściowo w czasie wykonywania.

## <a name="register-the-language-service-by-using-attributes"></a>Rejestrowanie usługi językowej przy użyciu atrybutów
 Następujące atrybuty są używane do rejestrowania usługi językowej.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  Te atrybuty są wyjaśnione poniżej

### <a name="provideserviceattribute"></a>ProvideServiceAttribute
 Ten atrybut rejestruje usługę językową jako usługę.

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
 Ten atrybut rejestruje usługę językową, w odniesieniu do usługi językowej. Umożliwia ustawienie opcji, które określają funkcje oferowane przez usługę języka. W przykładzie przedstawiono podzestaw opcji, które usługa języka może podać. Aby zapoznać się z pełnym zestawem opcji usługi językowej, zobacz <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> .

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
 Ten atrybut kojarzy usługę języka z rozszerzeniem pliku. Za każdym razem, gdy plik z tym rozszerzeniem jest ładowany, usługa języka jest uruchamiana i używana do wyświetlania zawartości pliku.

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
 Ten atrybut rejestruje lokalizację, z której uzyskuje się szablony rozszerzenia lub fragmentu kodu. Te informacje są używane przez **przeglądarkę fragmentów kodu** i Edytor po wstawieniu fragmentu kodu do pliku źródłowego.

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
 Ten atrybut rejestruje stronę właściwości, która zostanie wyświetlona w oknie dialogowym **Opcje** w kategorii **Edytor tekstu** . Użyj jednego z tych atrybutów dla każdej strony, która ma być wyświetlana dla usługi językowej. Jeśli musisz zorganizować strony w strukturze drzewa, użyj dodatkowych atrybutów, aby zdefiniować każdy węzeł drzewa.

### <a name="example"></a>Przykład
 Ten przykład przedstawia dwie strony właściwości, **Opcje** i **wcięcia**oraz jeden węzeł, który zawiera drugą stronę właściwości.

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

## <a name="proffer-the-language-service-at-run-time"></a>Udąło usługę języka w czasie wykonywania
 Po załadowaniu pakietu językowego należy sprawdzić [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , czy usługa języka jest gotowa. Można to zrobić przez proffering usługi. Jest to wykonywane w <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodzie. Ponadto należy uruchomić czasomierz, który wywołuje usługę języka w okresach bezczynności, aby można było wykonać analizę w tle. Ten czasomierz bezczynności służy również do aktualizowania właściwości dokumentu, jeśli zostały zaimplementowane za pomocą <xref:Microsoft.VisualStudio.Package.DocumentProperties> klasy. Aby można było obsługiwać czasomierz, pakiet musi implementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> interfejs (tylko <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> Metoda musi być w pełni zaimplementowana; pozostałe metody mogą zwracać wartości domyślne).

### <a name="example"></a>Przykład
 W tym przykładzie przedstawiono typowe podejście do proffering usługi i dostarczania czasomierza bezczynności.

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
