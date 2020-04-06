---
title: Tworzenie rozszerzenia za pomocą pakietu VSPackage | Dokumenty firmy Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1037ebcc58cc4183e6f02119bc7b46abfc132f52
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739525"
---
# <a name="create-an-extension-with-a-vspackage"></a>Tworzenie rozszerzenia za pomocą pakietu VSPackage

W tym przewodniku pokazano, jak utworzyć projekt VSIX i dodać element projektu VSPackage. Użyjemy VSPackage, aby uzyskać usługę powłoki interfejsu użytkownika w celu wyświetlenia okna komunikatu.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>Tworzenie pakietu VSPackage

1. Utwórz projekt VSIX o nazwie **FirstPackage**. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt,** wyszukując "vsix".

2. Po otwarciu projektu dodaj szablon elementu pakietu programu Visual Studio o nazwie **FirstPackage**. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. W oknie dialogowym **Dodawanie nowego elementu** przejdź do pozycji**Rozszerzalność** **programu Visual C#** > i wybierz pozycję **Pakiet programu Visual Studio**. W polu **Nazwa** u dołu okna zmień nazwę pliku polecenia na *FirstPackage.cs*.

3. Skompiluj projekt i rozpocznij debugowanie.

    Pojawi się eksperymentalne wystąpienie programu Visual Studio. Aby uzyskać więcej informacji na temat wystąpienia eksperymentalnego, zobacz [Wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).

4. W wystąpieniu eksperymentalnym otwórz okno**Rozszerzenia i aktualizacje** **narzędzi.** >  W tym miejscu powinno zostać wyświetlene rozszerzenie **FirstPackage.** (Jeśli otworzysz **rozszerzenia i aktualizacje** w wystąpieniu roboczym programu Visual Studio, nie zobaczysz **funkcji FirstPackage).**

## <a name="load-the-vspackage"></a>Załaduj pakiet VSPackage

W tym momencie rozszerzenie nie ładuje się, ponieważ nie ma nic, co powoduje, że do załadowania. Zazwyczaj można załadować rozszerzenie podczas interakcji z jego interfejsu użytkownika (kliknięcie polecenia menu, otwarcie okna narzędzia) lub określając, że VSPackage należy załadować w określonym kontekście interfejsu użytkownika. Aby uzyskać więcej informacji na temat ładowania vspackages i kontekstów interfejsu użytkownika, zobacz [Ładowanie VSPackages](../extensibility/loading-vspackages.md). W tej procedurze pokażemy, jak załadować VSPackage, gdy rozwiązanie jest otwarte.

1. Otwórz plik *FirstPackage.cs.* Poszukaj deklaracji `FirstPackage` klasy. Zastąp istniejące atrybuty następującymi atrybutami:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Dodajmy komunikat, który informuje nas, że vspackage został załadowany. Używamy `Initialize()` metody VSPackage, aby to zrobić, ponieważ można uzyskać usługi Visual Studio tylko po vsPackage został umiejscowiony. (Aby uzyskać więcej informacji na temat uzyskiwania usług, zobacz [Jak: Pobierz usługę](../extensibility/how-to-get-a-service.md).) `Initialize()` Zastąp `FirstPackage` metodę z <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> kodem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> który pobiera usługę, pobiera interfejs i wywołuje jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> metodę.

    ```csharp
    protected override void Initialize()
    {
        base.Initialize();

        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(
            0,
            ref clsid,
            "FirstPackage",
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result));
    }
    ```

3. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.

4. Otwórz rozwiązanie w wystąpieniu eksperymentalnym. Powinno zostać wyświetlone okno komunikatu **z komunikatem Pierwszy pakiet wewnątrz inicjowania()**.
