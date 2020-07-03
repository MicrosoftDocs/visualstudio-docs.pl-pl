---
title: Tworzenie rozszerzenia za pomocą pakietu VSPackage | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68ade2f8d334c1f93349e396d910fa300f6b5417
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903859"
---
# <a name="create-an-extension-with-a-vspackage"></a>Tworzenie rozszerzenia za pomocą pakietu VSPackage

W tym instruktażu pokazano, jak utworzyć projekt VSIX i dodać element projektu pakietu VSPackage. Będziemy używać pakietu VSPackage, aby pobrać usługę powłoki interfejsu użytkownika w celu wyświetlenia okna komunikatu.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>Utwórz pakietu VSPackage

1. Utwórz projekt VSIX o nazwie **FirstPackage**. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** , wyszukując frazę "VSIX".

2. Po otwarciu projektu Dodaj szablon elementu pakietu programu Visual Studio o nazwie **FirstPackage**. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**. W oknie dialogowym **Dodaj nowy element** przejdź do rozszerzalności **Visual C#**  >  **Extensibility** i wybierz pozycję **pakiet programu Visual Studio**. W polu **Nazwa** w dolnej części okna Zmień nazwę pliku polecenia na *FirstPackage.cs*.

3. Skompiluj projekt i Rozpocznij debugowanie.

    Pojawia się eksperymentalne wystąpienie programu Visual Studio. Aby uzyskać więcej informacji o wystąpieniu eksperymentalnym, zobacz [wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).

4. W eksperymentalnym wystąpieniu Otwórz okno **Narzędzia**  >  **rozszerzenia i aktualizacje** . Tutaj powinno być widoczne rozszerzenie **FirstPackage** . (Jeśli otworzysz **rozszerzenia i aktualizacje** w działającym wystąpieniu programu Visual Studio, nie zobaczysz **FirstPackage**).

## <a name="load-the-vspackage"></a>Załaduj pakietu VSPackage

W tym momencie rozszerzenie nie jest ładowane, ponieważ nie ma nic, co spowoduje jego załadowanie. Można ogólnie załadować rozszerzenie podczas korzystania z jego interfejsu użytkownika (klikając polecenie menu, otwierając okno narzędzia) lub określając, że pakietu VSPackage powinno zostać załadowane w określonym kontekście interfejsu użytkownika. Aby uzyskać więcej informacji na temat ładowania pakietów VSPackage i kontekstów interfejsu użytkownika, zobacz [ładowanie pakietów VSPackage](../extensibility/loading-vspackages.md). W tej procedurze pokazano, jak załadować pakietu VSPackage, gdy rozwiązanie jest otwarte.

1. Otwórz plik *FirstPackage.cs* . Poszukaj deklaracji `FirstPackage` klasy. Zastąp istniejące atrybuty następującymi atrybutami:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Dodajmy komunikat informujący o tym, że pakietu VSPackage został załadowany. W tym celu używamy `Initialize()` metody pakietu VSPackage, ponieważ usługi Visual Studio można uzyskać dopiero po zlokalizowaniu pakietu VSPackage. (Aby uzyskać więcej informacji na temat pobierania usług, zobacz [How to: get a Service](../extensibility/how-to-get-a-service.md)). Zastąp `Initialize()` metodę `FirstPackage` kodem, który pobiera <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> usługę, pobiera <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfejs i wywołuje jego <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> metodę.

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

3. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.

4. Otwórz rozwiązanie w eksperymentalnym wystąpieniu. Powinien zostać wyświetlony komunikat z informacją, że **pierwszy pakiet znajduje się w polu Initialize ()**.
