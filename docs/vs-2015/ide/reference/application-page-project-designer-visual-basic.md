---
title: Strona aplikacji, Projektant projektu (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: 8cec9fea-cd92-47ff-88dd-7c928f0b4a74
caps.latest.revision: 68
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 893647303b493ea633caf076658edbdcf0664ccc
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850835"
---
# <a name="application-page-project-designer-visual-basic"></a>Strona aplikacji, Projektant projektu (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użyj strony **aplikacji** projektanta projektu, aby określić ustawienia i właściwości aplikacji projektu.

 Aby uzyskać dostęp do strony **aplikacji** , wybierz węzeł projektu (nie węzeł **rozwiązania** ) w **Eksplorator rozwiązań**. Następnie wybierz **projekt**, **Właściwości** na pasku menu. Gdy pojawi się Projektant projektu, kliknij kartę **aplikacja** .

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="general-application-settings"></a>Ogólne ustawienia aplikacji
 Poniższe opcje umożliwiają skonfigurowanie ustawień ogólnych dla aplikacji.

 **Nazwa zestawu** Określa nazwę pliku wyjściowego, który będzie zawierać manifest zestawu. W przypadku zmiany tej właściwości zostanie również zmieniona właściwość **Nazwa wyjściowa** . Możesz również wprowadzić tę zmianę w wierszu polecenia przy użyciu [/out (Visual Basic)](https://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae). Aby uzyskać informacje o tym, jak uzyskać programowo dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

 **Główna przestrzeń nazw** Określa podstawową przestrzeń nazw dla wszystkich plików w projekcie. Na przykład jeśli ustawisz **główną przestrzeń nazw** na `Project1` i masz `Class1` poza obszarem nazw w kodzie, jego przestrzeń nazw byłaby `Project1.Class1`. Jeśli masz `Class2` w przestrzeni nazw `Order` w kodzie, jego przestrzeń nazw byłaby `Project1.Order.Class2`.

 Jeśli wyczyścisz **główną przestrzeń nazw**, możesz określić strukturę przestrzeni nazw projektu w kodzie.

> [!NOTE]
> Jeśli używasz słowa kluczowego Global w [instrukcji Namespace](https://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2), możesz zdefiniować przestrzeń nazw poza główną przestrzenią nazw projektu. Jeśli wyczyścisz **główną przestrzeń nazw**, `Global` stać się przestrzenią nazw najwyższego poziomu, co spowoduje usunięcie słowa kluczowego `Global` w instrukcji `Namespace`. Aby uzyskać więcej informacji, zobacz "globalne słowo kluczowe w instrukcjach przestrzeni nazw" w [przestrzeniach nazw w Visual Basic](https://msdn.microsoft.com/library/cffac744-ab8c-4f1f-ba50-732c22ab4b88).

 Aby uzyskać informacje na temat sposobu tworzenia przestrzeni nazw w kodzie, zobacz temat [przestrzeń nazw](https://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2).

 Aby uzyskać więcej informacji na temat właściwości głównej przestrzeni nazw, zobacz [/RootNamespace —](https://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783).

 Aby uzyskać informacje o tym, jak uzyskać programowo dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

 **Platforma docelowa (wszystkie konfiguracje)** Określa wersję .NET Framework, do której należy aplikacja. Ta opcja może mieć różne wartości w zależności od wersji .NET Framework zainstalowanych na komputerze.

 Wartość domyślna jest zgodna z platformą docelową określoną w oknie dialogowym **Nowy projekt** .

> [!NOTE]
> Wstępnie wymagane pakiety wymienione w [oknie dialogowym wymagania wstępne](../../ide/reference/prerequisites-dialog-box.md) są ustawiane automatycznie po otwarciu okna dialogowego po raz pierwszy. Jeśli później zmienisz platformę docelową projektu, musisz ręcznie określić warunki wstępne, aby dopasować ją do nowej platformy docelowej.

 Aby uzyskać więcej informacji, zobacz [How to: Targeting](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) a [Visual Studio — omówienie wielu](../../ide/visual-studio-multi-targeting-overview.md).NET Framework elementów docelowych.

 **Typ aplikacji** Określa typ aplikacji do skompilowania. W przypadku aplikacji [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] można określić **aplikację ze sklepu Windows**, **bibliotekę klas**lub **plik WinMD**. W przypadku większości innych typów aplikacji można określić **aplikację systemu Windows**, **aplikację konsolową**, **bibliotekę klas**, **usługę systemu Windows**lub **bibliotekę formantów sieci Web**.

 Dla projektu aplikacji sieci Web należy określić **bibliotekę klas**.

 W przypadku określenia opcji **pliku winmd** typy mogą być rzutowane na dowolny język programowania środowisko wykonawcze systemu Windows. Przez pakowanie danych wyjściowych projektu jako pliku WinMD, można zakodować aplikację w wielu językach i współdziałać z kodem, tak jakby były one napisane w tym samym języku. Możesz użyć opcji **pliku winmd** dla rozwiązań przeznaczonych dla bibliotek środowisko wykonawcze systemu Windows, w tym [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [Tworzenie składników Środowisko wykonawcze systemu Windows C# w i Visual Basic](https://msdn.microsoft.com/library/windows/apps/br230301(v=VS.85).aspx).

> [!NOTE]
> Środowisko wykonawcze systemu Windows można projektować typów, tak aby były one widoczne jako obiekty natywne w zależności od używanego języka. Na przykład aplikacje JavaScript, które współpracują z środowisko wykonawcze systemu Windows używają go jako zestawu obiektów JavaScript, a C# aplikacje używają biblioteki jako kolekcji obiektów .NET. Przez pakowanie danych wyjściowych projektu jako pliku WinMD można skorzystać z tej samej technologii, która środowisko wykonawcze systemu Windows używa.

 Aby uzyskać więcej informacji na temat właściwości **typu aplikacji** , zobacz [/Target (Visual Basic)](https://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c). Aby uzyskać informacje o tym, jak uzyskać programowo dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.OutputType%2A>.

 **Ikona** Ustawia plik ICO, który ma być używany jako ikona programu. Wybierz pozycję **\<Przeglądaj... >** przeglądać istniejącej grafiki. Aby uzyskać więcej informacji, zobacz [/win32icon](https://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) (lub [/Win32icon (C# opcje kompilatora)](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138). Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

 **Formularz startowy/obiekt startowy/początkowy identyfikator URI** Określa formularz startowy lub punkt wejścia aplikacji.

 Jeśli wybrano opcję **Włącz platformę aplikacji** (domyślnie), ta lista jest zatytułowana **formularz startowy** i pokazuje tylko formularze, ponieważ struktura aplikacji obsługuje tylko formularze uruchamiania, a nie obiekty.

 Jeśli projekt jest aplikacją przeglądarki WPF, na liście jest **uruchamiany początkowy identyfikator URI**, a wartością domyślną jest **Strona1. XAML**. Lista **początkowy identyfikator URI** umożliwia określenie zasobu interfejsu użytkownika (elementu XAML), który będzie wyświetlany podczas uruchamiania aplikacji. Aby uzyskać więcej informacji, zobacz temat <xref:System.Windows.Application.StartupUri%2A>.

 Jeśli opcja **Włącz platformę aplikacji** jest wyczyszczona, ta lista będzie **obiektem startowym** i pokazuje formularze oraz klasy lub moduły z `Sub Main`.

 **Obiekt startowy** definiuje punkt wejścia, który ma być wywoływany, gdy aplikacja jest ładowana. Zwykle jest to ustawienie w formularzu głównym w aplikacji lub do procedury `Sub Main`, która ma być uruchamiana podczas uruchamiania aplikacji. Ponieważ biblioteki klas nie mają punktu wejścia, ich jedyną opcją dla tej właściwości jest **(None)** . Aby uzyskać więcej informacji, zobacz [/Main](https://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0). Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

 **Informacje o zestawie** Kliknij ten przycisk, aby wyświetlić okno [dialogowe informacje o zestawie](../../ide/reference/assembly-information-dialog-box.md).

 **Włącz platformę aplikacji** Określa, czy projekt będzie używać struktury aplikacji. Ustawienie tej opcji ma wpływ na opcje dostępne w **formularzu startowym**/**obiekcie startowym**.

 Jeśli to pole wyboru jest zaznaczone, aplikacja używa standardowej `Sub Main`. Zaznaczenie tego pola wyboru włącza funkcje w sekcji **Właściwości platformy aplikacji systemu Windows** , a także wymaga wybrania formularza startowego.

 Jeśli to pole wyboru jest wyczyszczone, aplikacja używa niestandardowego `Sub Main` określonego w **formularzu startowym**. W takim przypadku można określić obiekt uruchamiania (niestandardowy `Sub Main` w metodzie lub klasie) albo w formularzu. Ponadto opcje w sekcji **Właściwości platformy aplikacji systemu Windows** stają się niedostępne.

 **Wyświetl ustawienia systemu Windows** Kliknij ten przycisk, aby wygenerować i otworzyć plik App. manifest. Program Visual Studio używa tego pliku do generowania danych manifestu dla aplikacji. Następnie ustaw poziom wykonywania żądany przez funkcję Kontrola konta użytkownika, modyfikując tag `<requestedExecutionLevel>` w pliku App. manifest w następujący sposób:

 `<requestedExecutionLevel level="asInvoker" />`

 Technologia ClickOnce działa z poziomem `asInvoker` lub w trybie zwirtualizowanym (bez generowania manifestu). Aby określić tryb zwirtualizowany, usuń cały tag z pliku App. manifest.

 Aby uzyskać więcej informacji na temat generowania manifestu, zobacz [wdrażanie ClickOnce w systemie Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Właściwości struktury aplikacji systemu Windows
 Poniższe ustawienia są dostępne w sekcji **Właściwości platformy aplikacji systemu Windows** . Te opcje są dostępne tylko wtedy, gdy zaznaczone jest pole wyboru **Włącz platformę aplikacji** . W poniższej sekcji opisano ustawienia **Właściwości platformy aplikacji systemu Windows** dla aplikacji Windows Presentation Foundation (WPF).

 **Włącz style wizualne XP** Włącza lub wyłącza style wizualne systemu Windows XP, znane także jako *motywy systemu Windows XP*. Style wizualne systemu Windows XP umożliwiają na przykład kontrolki z zaokrąglonymi rogami i kolorami dynamicznymi. Wartość domyślna jest włączona. Aby uzyskać więcej informacji na temat stylów wizualnych systemu Windows XP, zobacz [funkcje systemu Windows XP i kontrolki Windows Forms](https://msdn.microsoft.com/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0).

 **Tworzenie aplikacji z pojedynczym wystąpieniem** Zaznacz to pole wyboru, aby uniemożliwić użytkownikom uruchamianie wielu wystąpień aplikacji. Ustawienie domyślne dla tego pola wyboru jest wyczyszczone. To ustawienie umożliwia uruchomienie wielu wystąpień aplikacji.

 **Zapisz my. Settings przy zamykaniu** Zaznacz to pole wyboru, aby określić, że ustawienia `My.Settings` aplikacji są zapisywane, gdy użytkownicy zamkną komputery. Ustawienie domyślne jest włączone. Jeśli ta opcja jest wyłączona, można ręcznie zapisać ustawienia aplikacji, wywołując `My.Settings.Save`.

 **Tryb uwierzytelniania** Wybierz pozycję **Windows** (domyślnie), aby określić użycie uwierzytelniania systemu Windows w celu zidentyfikowania aktualnie zalogowanego użytkownika. Te informacje można pobrać w czasie wykonywania przy użyciu obiektu `My.User`. Wybierz pozycję **aplikacja — zdefiniowana** , jeśli będziesz udostępniać własny kod do uwierzytelniania użytkowników zamiast korzystać z domyślnych metod uwierzytelniania systemu Windows.

 **Tryb zamykania** Zaznacz **po zamknięciu formularza startowego** (wartość domyślna), aby określić, że aplikacja kończy działanie, gdy formularz zostanie zamknięty, nawet jeśli inne formularze są otwarte. Zaznacz pole **podczas zamykania ostatniego formularza** , aby określić, że aplikacja kończy działanie, gdy ostatni formularz jest zamknięty lub kiedy `My.Application.Exit` lub instrukcja `End` jest wywoływana jawnie.

 Wybierz pozycję **przy jawnym zamknięciu** , aby określić, że aplikacja kończy działanie, gdy jawnie wywołasz `Shutdown`.

 Wybierz pozycję **przy ostatnim oknie Zamknij** , aby określić, że aplikacja kończy się po zamknięciu ostatniego okna lub w przypadku jawnego wywołania `Shutdown`. To jest ustawienie domyślne.

 Wybierz pozycję **w oknie głównym Zamknij** , aby określić, że aplikacja kończy się po zamknięciu okna głównego lub w przypadku jawnego wywołania `Shutdown`.

 **Ekran powitalny** Wybierz formularz, który ma być używany jako ekran powitalny. Należy wcześniej utworzyć ekran powitalny przy użyciu formularza lub szablonu. Wartość domyślna to **(brak)** .

 **Wyświetlanie zdarzeń aplikacji** Kliknij ten przycisk, aby wyświetlić plik kodu zdarzeń, w którym można napisać zdarzenia dla zdarzeń struktury aplikacji `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` i `NetworkAvailabilityChanged`. Można również zastąpić niektóre metody struktury aplikacji. Na przykład możesz zmienić zachowanie wyświetlania ekranu powitalnego, zastępując `OnInitialize`.

### <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-applications"></a>Właściwości struktury aplikacji systemu Windows dla aplikacji Windows Presentation Foundation (WPF)
 Poniższe ustawienia są dostępne w sekcji **Właściwości platformy aplikacji systemu Windows** , gdy projekt jest aplikacją Windows Presentation Foundation. Te opcje są dostępne tylko wtedy, gdy zaznaczone jest pole wyboru **Włącz platformę aplikacji** . Opcje wymienione w tej tabeli są dostępne tylko dla aplikacji WPF lub aplikacji przeglądarki WPF. Nie są one dostępne dla formantów użytkownika WPF ani bibliotek formantów niestandardowych.

 **Tryb zamykania** Ta właściwość ma zastosowanie tylko do aplikacji Windows Presentation Foundation.

 Wybierz pozycję **przy jawnym zamknięciu** , aby określić, że aplikacja kończy działanie, gdy jawnie wywołasz <xref:System.Windows.Application.Shutdown%2A>.

 Wybierz pozycję **przy ostatnim oknie Zamknij** , aby określić, że aplikacja kończy się po zamknięciu ostatniego okna lub w przypadku jawnego wywołania <xref:System.Windows.Application.Shutdown%2A>. To jest ustawienie domyślne.

 Wybierz pozycję **w oknie głównym Zamknij** , aby określić, że aplikacja kończy się po zamknięciu okna głównego lub w przypadku jawnego wywołania <xref:System.Windows.Application.Shutdown%2A>.

 Aby uzyskać więcej informacji o korzystaniu z tego ustawienia, zobacz <xref:System.Windows.Application.Shutdown%2A>

 **Edytuj kod XAML** Kliknij ten przycisk, aby otworzyć i zmodyfikować plik definicji aplikacji (Application. XAML) w edytorze XAML. Po kliknięciu tego przycisku aplikacja. XAML zostanie otwarta w węźle definicja aplikacji. Może być konieczne edytowanie tego pliku, aby wykonać określone zadania, takie jak Definiowanie zasobów. Jeśli plik definicji aplikacji nie istnieje, Projektant projektu tworzy jeden.

 **Wyświetlanie zdarzeń aplikacji** Kliknij ten przycisk, aby wyświetlić `Application` plik klasy częściowej (Application. XAML. vb) w edytorze kodu. Jeśli plik nie istnieje, Projektant projektu tworzy jeden z odpowiednią nazwą klasy i przestrzenią nazw.

 Obiekt <xref:System.Windows.Application> zgłasza zdarzenia, gdy wystąpią zmiany stanu aplikacji (na przykład podczas uruchamiania lub zamykania aplikacji). Aby zapoznać się z pełną listą zdarzeń uwidacznianych przez tę klasę, zobacz <xref:System.Windows.Application>. Te zdarzenia są obsługiwane w sekcji kod użytkownika klasy częściowej `Application`.

## <a name="see-also"></a>Zobacz też
[Zarządzanie właściwościami aplikacji](../../ide/application-properties.md) [pisanie kodu w rozwiązaniach pakietu Office](https://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)
