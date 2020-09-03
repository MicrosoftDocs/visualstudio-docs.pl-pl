---
title: Strona aplikacji właściwości projektu VB
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe303f86b282e7e803dacc1dd8f4d3c1d6b72121
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595816"
---
# <a name="application-page-project-designer-visual-basic"></a>Strona aplikacji, Projektant projektu (Visual Basic)

Użyj strony **aplikacji** projektanta projektu, aby określić ustawienia i właściwości aplikacji projektu.

Aby uzyskać dostęp do strony **aplikacji** , wybierz węzeł projektu (nie węzeł **rozwiązania** ) w **Eksplorator rozwiązań**. Następnie wybierz **Project**  >  **Właściwości** projektu na pasku menu. Gdy zostanie wyświetlony **Projektant projektu** , wybierz kartę **aplikacja** .

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Ogólne ustawienia aplikacji

Poniższe opcje umożliwiają skonfigurowanie ustawień ogólnych dla aplikacji.

### <a name="assembly-name"></a>Nazwa zestawu

Określa nazwę pliku wyjściowego, który będzie zawierać manifest zestawu. Zmiana tej właściwości spowoduje również zmianę właściwości **Nazwa wyjściowa** .

Możesz również określić nazwę pliku wyjściowego z wiersza polecenia przy użyciu przełącznika kompilatora [/out (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out) .

Aby uzyskać informacje na temat programistycznego uzyskiwania dostępu do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.AssemblyName%2A> .

### <a name="root-namespace"></a>Główna przestrzeń nazw

Określa podstawową przestrzeń nazw dla wszystkich plików w projekcie. Na przykład, jeśli ustawisz **główną przestrzeń nazw** na `Project1` , a będziesz mieć `Class1` poza przestrzenią nazw w kodzie, jej przestrzeń nazw byłaby `Project1.Class1` . Jeśli `Class2` w kodzie znajduje się w przestrzeni `Order` nazw, jej przestrzeń nazw byłaby `Project1.Order.Class2` .

Jeśli wyczyścisz **główną przestrzeń nazw**, możesz określić strukturę przestrzeni nazw projektu w kodzie.

> [!NOTE]
> Jeśli używasz `Global` słowa kluczowego w [instrukcji Namespace](/dotnet/visual-basic/language-reference/statements/namespace-statement), możesz zdefiniować przestrzeń nazw spoza głównej przestrzeni nazw projektu. Jeśli wyczyścisz **główną przestrzeń nazw**, `Global` to przestrzeń nazw najwyższego poziomu, która usunie potrzebę `Global` słowa kluczowego w `Namespace` instrukcji. Aby uzyskać więcej informacji, zobacz "globalne słowo kluczowe w instrukcjach przestrzeni nazw" w [przestrzeniach nazw w Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces).

Aby uzyskać informacje na temat sposobu tworzenia przestrzeni nazw w kodzie, zobacz temat [przestrzeń nazw](/dotnet/visual-basic/language-reference/statements/namespace-statement).

Aby uzyskać więcej informacji na temat właściwości głównej przestrzeni nazw, zobacz [/RootNamespace —](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Aby uzyskać informacje na temat programistycznego uzyskiwania dostępu do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.RootNamespace%2A> .

### <a name="target-framework-all-configurations"></a>Platforma docelowa (wszystkie konfiguracje)

Określa wersję programu .NET, która jest przeznaczona dla aplikacji. Ta opcja może mieć różne wartości w zależności od tego, które wersje platformy .NET są zainstalowane na komputerze.

W przypadku projektów .NET Framework wartość domyślna jest zgodna z platformą docelową, która została określona podczas tworzenia projektu.

> [!NOTE]
> Wstępnie wymagane pakiety wymienione w [oknie dialogowym wymagania wstępne](../../ide/reference/prerequisites-dialog-box.md) są ustawiane automatycznie po otwarciu okna dialogowego po raz pierwszy. Jeśli później zmienisz platformę docelową projektu, musisz ręcznie określić warunki wstępne, aby dopasować ją do nowej platformy docelowej.

Aby uzyskać więcej informacji, zobacz temat [Omówienie funkcji określania wartości docelowej](../../ide/visual-studio-multi-targeting-overview.md).

### <a name="application-type"></a>Typ aplikacji

Określa typ aplikacji do skompilowania. Wartości są różne w zależności od typu projektu. Na przykład dla projektu **aplikacji Windows Forms** można określić **aplikację Windows Forms**, **bibliotekę klas**, **aplikację konsolową**, **usługę systemu Windows**lub **bibliotekę formantów sieci Web**.

Dla projektu aplikacji sieci Web należy określić **bibliotekę klas**.

Aby uzyskać więcej informacji na temat właściwości **typu aplikacji** , zobacz [/Target (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Aby uzyskać informacje o tym, jak uzyskać programowo dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.OutputType%2A> .

### <a name="auto-generate-binding-redirects"></a>Automatyczne generowanie przekierowań powiązań

Przekierowania powiązań są dodawane do projektu, jeśli aplikacja lub jej składniki odwołują się do więcej niż jednej wersji tego samego zestawu. Jeśli chcesz ręcznie zdefiniować przekierowania powiązań w pliku projektu, usuń zaznaczenie opcji **automatycznie Generuj przekierowania powiązań**.

Aby uzyskać więcej informacji na temat przekierowania, zobacz Przekierowywanie [wersji zestawu](/dotnet/framework/configure-apps/redirect-assembly-versions).

### <a name="startup-form--startup-object--startup-uri"></a>Formularz startowy/obiekt startowy/początkowy identyfikator URI

Określa formularz startowy lub punkt wejścia aplikacji.

Jeśli wybrano opcję **Włącz platformę aplikacji** (domyślnie), ta lista jest zatytułowana **formularz startowy** i pokazuje tylko formularze, ponieważ struktura aplikacji obsługuje tylko formularze uruchamiania, a nie obiekty.

Jeśli projekt jest aplikacją przeglądarki WPF, na liście jest **uruchamiany początkowy identyfikator URI**, a wartością domyślną jest **Strona1. XAML**. Lista **początkowy identyfikator URI** umożliwia określenie zasobu interfejsu użytkownika (elementu XAML), który będzie wyświetlany podczas uruchamiania aplikacji. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Application.StartupUri%2A>.

Jeśli opcja **Włącz platformę aplikacji** jest wyczyszczona, ta lista będzie **obiektem startowym** i pokazuje formularze oraz klasy lub moduły z `Sub Main` .

**Obiekt startowy** definiuje punkt wejścia, który ma być wywoływany, gdy aplikacja jest ładowana. Zwykle jest to ustawienie w formularzu głównym w aplikacji lub do `Sub Main` procedury, która ma być uruchamiana podczas uruchamiania aplikacji. Ponieważ biblioteki klas nie mają punktu wejścia, ich jedyną opcją dla tej właściwości jest **(None)**. Aby uzyskać więcej informacji, zobacz [/Main](/dotnet/visual-basic/reference/command-line-compiler/main). Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.StartupObject%2A> .

### <a name="icon"></a>Ikona

Ustawia plik ICO, który ma być używany jako ikona programu. Wybierz **\<Browse...>** , aby przeglądać w poszukiwaniu istniejącej grafiki. Aby uzyskać więcej informacji, zobacz [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (lub [/Win32icon (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)). Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A> .

### <a name="assembly-information"></a>Informacje o zestawie

Kliknij ten przycisk, aby wyświetlić okno [dialogowe informacje o zestawie](../../ide/reference/assembly-information-dialog-box.md).

### <a name="enable-application-framework"></a>Włącz platformę aplikacji

Określa, czy projekt będzie używać struktury aplikacji. Ustawienie tej opcji ma wpływ na opcje dostępne w **Startup form** / **obiekcie startowym**formularza startowego.

Jeśli to pole wyboru jest zaznaczone, aplikacja używa standardu `Sub Main` . Zaznaczenie tego pola wyboru włącza funkcje w sekcji **Właściwości platformy aplikacji systemu Windows** , a także wymaga wybrania formularza startowego.

Jeśli to pole wyboru jest wyczyszczone, aplikacja używa niestandardowego, `Sub Main` który został określony w **formularzu startowym**. W takim przypadku można określić obiekt uruchamiania (niestandardowy `Sub Main` w metodzie lub klasie) lub w formularzu. Ponadto opcje w sekcji **Właściwości platformy aplikacji systemu Windows** stają się niedostępne.

### <a name="view-windows-settings"></a>Wyświetl ustawienia systemu Windows

Kliknij ten przycisk, aby wygenerować i otworzyć plik *App. manifest* . Program Visual Studio używa tego pliku do generowania danych manifestu dla aplikacji. Następnie ustaw poziom wykonywania żądany przez funkcję Kontrola konta użytkownika, modyfikując `<requestedExecutionLevel>` tag w pliku *App. manifest* w następujący sposób:

`<requestedExecutionLevel level="asInvoker" />`

Technologia ClickOnce działa z poziomem `asInvoker` lub w trybie zwirtualizowanym (bez generowania manifestu). Aby określić tryb zwirtualizowany, usuń cały tag z pliku App. manifest.

Aby uzyskać więcej informacji na temat generowania manifestu, zobacz [wdrażanie ClickOnce w systemie Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Właściwości struktury aplikacji systemu Windows

Poniższe ustawienia są dostępne w sekcji **Właściwości platformy aplikacji systemu Windows** . Te opcje są dostępne tylko wtedy, gdy zaznaczone jest pole wyboru **Włącz platformę aplikacji** .

> [!TIP]
> W poniższej sekcji opisano ustawienia **Właściwości platformy Windows Framework** specyficzne dla aplikacji Windows Presentation Foundation (WPF).

### <a name="enable-xp-visual-styles"></a>Włącz style wizualne XP

Włącza lub wyłącza style wizualne systemu Windows XP, znane także jako *motywy systemu Windows XP*. Style wizualne systemu Windows XP umożliwiają na przykład kontrolki z zaokrąglonymi rogami i kolorami dynamicznymi. Wartość domyślna jest włączona.

### <a name="make-single-instance-application"></a>Tworzenie aplikacji z pojedynczym wystąpieniem

Zaznacz to pole wyboru, aby uniemożliwić użytkownikom uruchamianie wielu wystąpień aplikacji. Ustawienie domyślne dla tego pola wyboru jest *wyczyszczone*, co umożliwia uruchomienie wielu wystąpień aplikacji. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> zdarzenie.

### <a name="save-mysettings-on-shutdown"></a>Zapisz my. Settings przy zamykaniu

Zaznacz to pole wyboru, aby określić, że `My.Settings` Ustawienia aplikacji są zapisywane, gdy użytkownicy zamkną komputery. Ustawienie domyślne jest włączone. Jeśli ta opcja jest wyłączona, można ręcznie zapisać ustawienia aplikacji, wywołując polecenie `My.Settings.Save` .

### <a name="authentication-mode"></a>Tryb uwierzytelniania

Wybierz pozycję **Windows** (domyślnie), aby określić użycie uwierzytelniania systemu Windows w celu zidentyfikowania aktualnie zalogowanego użytkownika. Te informacje można pobrać w czasie wykonywania przy użyciu `My.User` obiektu. Wybierz pozycję **aplikacja — zdefiniowana** , jeśli będziesz udostępniać własny kod do uwierzytelniania użytkowników zamiast korzystać z domyślnych metod uwierzytelniania systemu Windows.

### <a name="shutdown-mode"></a>Tryb zamykania

Zaznacz **po zamknięciu formularza startowego** (wartość domyślna), aby określić, że aplikacja kończy działanie, gdy formularz zostanie zamknięty, nawet jeśli inne formularze są otwarte. Zaznacz pole **podczas zamykania ostatniego formularza** , aby określić, że aplikacja kończy działanie, gdy ostatni formularz jest zamknięty lub kiedy `My.Application.Exit` `End` instrukcja jest wywoływana jawnie.

Wybierz pozycję **przy jawnym zamknięciu** , aby określić, że aplikacja kończy działanie po jawnie wywołaniu `Shutdown` .

Wybierz pozycję **przy ostatnim oknie Zamknij** , aby określić, że aplikacja kończy się po zamknięciu ostatniego okna lub w przypadku jawnego wywołania `Shutdown` . Jest to ustawienie domyślne.

Wybierz pozycję **w oknie głównym Zamknij** , aby określić, że aplikacja kończy się po zamknięciu okna głównego lub podczas jawnego wywoływania `Shutdown` .

### <a name="splash-screen"></a>Ekran powitalny

Wybierz formularz, który ma być używany jako ekran powitalny. Należy wcześniej utworzyć ekran powitalny przy użyciu formularza lub szablonu. Wartość domyślna to **(brak)**.

### <a name="view-application-events"></a>Wyświetlanie zdarzeń aplikacji

Kliknij ten przycisk, aby wyświetlić plik kodu zdarzeń, w którym można napisać zdarzenia dla zdarzeń struktury aplikacji `Startup` ,, `Shutdown` `UnhandledException` `StartupNextInstance` i `NetworkAvailabilityChanged` . Można również zastąpić niektóre metody struktury aplikacji. Na przykład można zmienić zachowanie wyświetlania ekranu powitalnego przez zastąpienie `OnInitialize` .

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>Właściwości struktury aplikacji systemu Windows dla aplikacji Windows Presentation Foundation (WPF)

Poniższe ustawienia są dostępne w sekcji **Właściwości platformy aplikacji systemu Windows** , gdy projekt jest aplikacją Windows Presentation Foundation (WPF). Te opcje są dostępne tylko wtedy, gdy zaznaczone jest pole wyboru **Włącz platformę aplikacji** . Opcje wymienione w tej tabeli są dostępne tylko dla aplikacji platformy WPF lub WPF. Nie są one dostępne dla formantów użytkownika WPF ani bibliotek formantów niestandardowych.

### <a name="shutdown-mode"></a>Tryb zamykania

Ta właściwość ma zastosowanie tylko do aplikacji Windows Presentation Foundation (WPF).

Wybierz pozycję **przy jawnym zamknięciu** , aby określić, że aplikacja kończy działanie po jawnie wywołaniu <xref:System.Windows.Application.Shutdown%2A> .

Wybierz pozycję **przy ostatnim oknie Zamknij** , aby określić, że aplikacja kończy się po zamknięciu ostatniego okna lub w przypadku jawnego wywołania <xref:System.Windows.Application.Shutdown%2A> . Jest to ustawienie domyślne.

Wybierz pozycję **w oknie głównym Zamknij** , aby określić, że aplikacja kończy się po zamknięciu okna głównego lub podczas jawnego wywoływania <xref:System.Windows.Application.Shutdown%2A> .

Aby uzyskać więcej informacji na temat korzystania z tego ustawienia, zobacz. <xref:System.Windows.Application.Shutdown%2A>

### <a name="edit-xaml"></a>Edytuj kod XAML

Ten przycisk otwiera plik definicji aplikacji (Application. XAML) w edytorze XAML. Po kliknięciu tego przycisku *aplikacja. XAML* zostanie otwarta w węźle definicja aplikacji. Może być konieczne edytowanie tego pliku, aby wykonać określone zadania, takie jak Definiowanie zasobów. Jeśli plik definicji aplikacji nie istnieje, Projektant projektu tworzy jeden.

### <a name="view-application-events"></a>Wyświetlanie zdarzeń aplikacji

Ten przycisk otwiera `Application` plik klasy (*Application. XAML. vb*) w edytorze kodu. Jeśli plik nie istnieje, Projektant projektu tworzy jeden z odpowiednią nazwą klasy i przestrzenią nazw.

<xref:System.Windows.Application>Obiekt zgłasza zdarzenia, gdy wystąpią zmiany stanu aplikacji (na przykład podczas uruchamiania lub zamykania aplikacji). Aby zapoznać się z pełną listą zdarzeń uwidacznianych przez tę klasę, zobacz <xref:System.Windows.Application> . Te zdarzenia są obsługiwane w sekcji kod użytkownika `Application` klasy częściowej.
