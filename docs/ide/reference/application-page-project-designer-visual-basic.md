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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595816"
---
# <a name="application-page-project-designer-visual-basic"></a>Strona aplikacji, Projektant projektu (Visual Basic)

Użyj **aplikacji** strony Projektanta projektu, aby określić ustawienia i właściwości aplikacji projektu.

Aby uzyskać dostęp do strony **Aplikacji,** wybierz węzeł projektu (a nie węzeł **Rozwiązanie)** w **Eksploratorze rozwiązań**. Następnie wybierz polecenie**Właściwości** **projektu** > na pasku menu. Po wyświetleniu **projektanta projektu** wybierz kartę **Aplikacja.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Ogólne ustawienia aplikacji

Poniższe opcje umożliwiają skonfigurowanie ustawień ogólnych dla aplikacji.

### <a name="assembly-name"></a>Nazwa zestawu

Określa nazwę pliku wyjściowego, który będzie zawierał manifest zestawu. Jeśli zmienisz tę właściwość, właściwość **Nazwa wyjściowa** również się zmieni.

Można również określić nazwę pliku wyjściowego z wiersza polecenia za pomocą przełącznika kompilatora [/out (Visual Basic).](/dotnet/visual-basic/reference/command-line-compiler/out)

Aby uzyskać informacje dotyczące programowego dostępu <xref:VSLangProj.ProjectProperties.AssemblyName%2A>do tej właściwości, zobacz .

### <a name="root-namespace"></a>Główny obszar nazw

Określa podstawową przestrzeń nazw dla wszystkich plików w projekcie. Na przykład, jeśli ustawisz `Project1` główny obszar `Class1` **nazw** i masz poza dowolnym obszarem nazw `Project1.Class1`w kodzie, jego obszar nazw będzie . Jeśli masz `Class2` w obszarze `Order` nazw w kodzie, `Project1.Order.Class2`jego obszar nazw będzie .

Jeśli wyczyścisz **główny obszar nazw,** można określić strukturę obszaru nazw projektu w kodzie.

> [!NOTE]
> Jeśli `Global` używasz słowa kluczowego w [instrukcji obszar nazw,](/dotnet/visual-basic/language-reference/statements/namespace-statement)można zdefiniować obszar nazw z głównego obszaru nazw projektu. Jeśli wyczyścisz **główny obszar nazw,** `Global` stanie się obszarem nazw najwyższego `Global` poziomu, `Namespace` który usuwa potrzebę słowa kluczowego w instrukcji. Aby uzyskać więcej informacji, zobacz "Globalne słowo kluczowe w instrukcjach obszaru nazw" w [obszarze nazw w języku Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces).

Aby uzyskać informacje dotyczące tworzenia obszarów nazw w kodzie, zobacz [Instrukcja obszaru nazw](/dotnet/visual-basic/language-reference/statements/namespace-statement).

Aby uzyskać więcej informacji na temat właściwości głównego obszaru nazw, zobacz [/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Aby uzyskać informacje dotyczące programowego dostępu <xref:VSLangProj.ProjectProperties.RootNamespace%2A>do tej właściwości, zobacz .

### <a name="target-framework-all-configurations"></a>Struktura docelowa (wszystkie konfiguracje)

Określa wersję platformy .NET przeznaczoną dla aplikacji. Ta opcja może mieć różne wartości w zależności od tego, które wersje platformy .NET są zainstalowane na komputerze.

W przypadku projektów programu .NET Framework wartość domyślna jest zgodna z platformą docelową określoną podczas tworzenia projektu.

> [!NOTE]
> Pakiety wymagań wstępnych, które są wymienione w [oknie dialogowym Wymagania wstępne](../../ide/reference/prerequisites-dialog-box.md) są ustawiane automatycznie po otwarciu okna dialogowego po raz pierwszy. Jeśli następnie zmienisz platformę docelową projektu, należy ręcznie określić wymagania wstępne, aby dopasować nową platformę docelową.

Aby uzyskać więcej informacji, zobacz [omówienie kierowania na ramy](../../ide/visual-studio-multi-targeting-overview.md).

### <a name="application-type"></a>Typ aplikacji

Określa typ aplikacji do utworzenia. Wartości różnią się w zależności od typu projektu. Na przykład dla projektu **aplikacji Windows Forms można** określić aplikację **Formularzy systemu Windows,** **bibliotekę klas**, aplikację **konsoli,** **usługę systemu Windows**lub **bibliotekę sterowania siecią Web**.

W przypadku projektu aplikacji sieci web należy określić **bibliotekę klas**.

Aby uzyskać więcej informacji na temat właściwości **Typ aplikacji,** zobacz [/target (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Aby uzyskać informacje o programowym dostępie <xref:VSLangProj.ProjectProperties.OutputType%2A>do tej właściwości, zobacz .

### <a name="auto-generate-binding-redirects"></a>Automatyczne generowanie przekierowań wiązania

Przekierowania powiązania są dodawane do projektu, jeśli aplikacja lub jej składniki odwołują się do więcej niż jednej wersji tego samego zestawu. Jeśli chcesz ręcznie zdefiniować przekierowania powiązania w pliku projektu, usuń zaznaczenie **przekierowywania powiązania autogeneruj**.

Aby uzyskać więcej informacji na temat przekierowania, zobacz [Przekierowywanie wersji zestawu](/dotnet/framework/configure-apps/redirect-assembly-versions).

### <a name="startup-form--startup-object--startup-uri"></a>Formularz startowy / Obiekt startowy / Identyfikator URI uruchamiania

Określa formularz startowy aplikacji lub punkt wejścia.

Jeśli wybrano opcję **Włącz strukturę aplikacji** (domyślnie), ta lista nosi tytuł **Formularz uruchamiania** i zawiera tylko formularze, ponieważ struktura aplikacji obsługuje tylko formularze startowe, a nie obiekty.

Jeśli projekt jest aplikacją przeglądarki WPF, ta lista nosi tytuł **Uruchamianie identyfikatora URI,** a domyślnie jest **Page1.xaml**. Lista **Uruchamianie identyfikatora URI** umożliwia określenie zasobu interfejsu użytkownika (elementu XAML), który aplikacja wyświetla po uruchomieniu aplikacji. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Application.StartupUri%2A>.

Jeśli **włącz platformę aplikacji** jest wyczyszczone, ta lista staje się **obiektem uruchamiania** i pokazuje zarówno formularze, jak i klasy lub moduły z programem `Sub Main`.

**Obiekt startowy** definiuje punkt wejścia, który ma być wywoływany podczas ładowania aplikacji. Ogólnie jest to ustawione na formularz główny w aplikacji `Sub Main` lub do procedury, która powinna być uruchamiana po uruchomieniu aplikacji. Ponieważ biblioteki klas nie mają punktu wejścia, ich jedyną opcją dla tej właściwości jest **(Brak)**. Aby uzyskać więcej informacji, zobacz [/main](/dotnet/visual-basic/reference/command-line-compiler/main). Aby uzyskać dostęp do tej <xref:VSLangProj.ProjectProperties.StartupObject%2A>właściwości programowo, zobacz .

### <a name="icon"></a>Ikona

Ustawia plik .ico, którego chcesz użyć jako ikony programu. Wybierz ** \<opcję Przeglądaj...>,** aby wyszukać istniejącą grafikę. Zobacz [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (lub [/win32icon (Opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)), aby uzyskać więcej informacji. Aby uzyskać dostęp do tej <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>właściwości programowo, zobacz .

### <a name="assembly-information"></a>Informacje o montażu

Kliknij ten przycisk, aby wyświetlić [okno dialogowe Informacje o złożeniu](../../ide/reference/assembly-information-dialog-box.md).

### <a name="enable-application-framework"></a>Włącz strukturę aplikacji

Określa, czy projekt będzie używał struktury aplikacji. Ustawienie tej opcji ma wpływ na opcje dostępne w**obiekcie Uruchamianie** **formularza**/.

Jeśli to pole wyboru jest zaznaczone, `Sub Main`aplikacja używa standardu . Zaznaczenie tego pola wyboru powoduje wyświetlenie funkcji w sekcji **właściwości struktury aplikacji systemu Windows,** a także wybranie formularza startowego.

Jeśli to pole wyboru jest wyczyszczone, `Sub Main` aplikacja używa niestandardowego określonego w **formularzu uruchamiania**. W takim przypadku można określić obiekt startowy (niestandardowy `Sub Main` w metodzie lub klasie) lub formularz. Ponadto opcje w sekcji **właściwości struktury aplikacji systemu Windows** stają się niedostępne.

### <a name="view-windows-settings"></a>Wyświetlanie ustawień systemu Windows

Kliknij ten przycisk, aby wygenerować i otworzyć plik *app.manifest.* Visual Studio używa tego pliku do generowania danych manifestu dla aplikacji. Następnie ustaw poziom wykonania żądanego konta `<requestedExecutionLevel>` użytkownika, modyfikując tag w *pliku app.manifest* w następujący sposób:

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce działa z `asInvoker` poziomem lub w trybie zwirtualizowanym (bez generowania manifestu). Aby określić tryb zwirtualizowany, usuń cały tag z pliku app.manifest.

Aby uzyskać więcej informacji na temat generowania manifestów, zobacz [ClickOnce Deployment w systemie Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Właściwości struktury aplikacji systemu Windows

Następujące ustawienia są dostępne w sekcji **właściwości struktury aplikacji systemu Windows.** Te opcje są dostępne tylko wtedy, gdy zaznaczone jest pole wyboru **Włącz strukturę aplikacji.**

> [!TIP]
> W poniższej sekcji opisano ustawienia **właściwości struktury aplikacji systemu Windows** specyficzne dla aplikacji Windows Presentation Foundation (WPF).

### <a name="enable-xp-visual-styles"></a>Włączanie stylów wizualnych PD

Włącza lub wyłącza style wizualne systemu Windows XP, znane również jako *Motywy systemu Windows XP*. Style wizualne systemu Windows XP umożliwiają na przykład kontrolki z zaokrąglonymi narożnikami i dynamicznymi kolorami. Wartość domyślna jest włączona.

### <a name="make-single-instance-application"></a>Tworzenie aplikacji z pojedynczym wystąpieniem

Zaznacz to pole wyboru, aby uniemożliwić użytkownikom uruchamianie wielu wystąpień aplikacji. Domyślne ustawienie tego pola wyboru jest *wyczyszczone,* co umożliwia uruchamianie wielu wystąpień aplikacji. Aby uzyskać więcej <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> informacji, zobacz zdarzenie.

### <a name="save-mysettings-on-shutdown"></a>Zapisz my.settings przy zamykaniu systemu

Zaznacz to pole wyboru, aby `My.Settings` określić, że ustawienia aplikacji są zapisywane, gdy użytkownicy zamykają swoje komputery. Ustawienie domyślne jest włączone. Jeśli ta opcja jest wyłączona, ustawienia aplikacji `My.Settings.Save`można zapisać ręcznie, dzwoniąc .

### <a name="authentication-mode"></a>Tryb uwierzytelniania

Wybierz **opcję Windows** (domyślnie), aby określić użycie uwierzytelniania systemu Windows do identyfikowania aktualnie zalogowanego użytkownika. Można pobrać te informacje w czasie `My.User` wykonywania przy użyciu obiektu. Wybierz **opcję Zdefiniowana przez aplikację,** jeśli udostępnisz własny kod do uwierzytelniania użytkowników zamiast domyślnych metod uwierzytelniania systemu Windows.

### <a name="shutdown-mode"></a>Tryb wyłączania

Wybierz **opcję Po zamknięciu formularza startowego** (domyślnie), aby określić, że aplikacja kończy działanie po zamknięciu formularza jako formularza startowego, nawet jeśli inne formularze są otwarte. Wybierz, **gdy ostatni formularz zamyka** się, aby określić, `My.Application.Exit` że `End` aplikacja kończy działanie, gdy ostatni formularz jest zamknięty lub kiedy lub instrukcja jest wywoływana jawnie.

Wybierz **opcję Jawne zamykanie,** aby określić, że aplikacja kończy działanie podczas jawnego wywoływania `Shutdown`.

Wybierz **na ostatnie okno blisko,** aby określić, że aplikacja kończy `Shutdown`się po zamknięciu ostatniego okna lub podczas jawnego wywołania . Jest to ustawienie domyślne.

Wybierz **w oknie głównym blisko,** aby określić, że zamknięcie aplikacji `Shutdown`po zamknięciu okna głównego lub jawnie wywołać .

### <a name="splash-screen"></a>Ekran powitalny

Wybierz formularz, którego chcesz użyć jako ekranu powitalnego. Wcześniej trzeba było utworzyć ekran powitalny przy użyciu formularza lub szablonu. Wartość domyślna **to (Brak)**.

### <a name="view-application-events"></a>Wyświetlanie zdarzeń aplikacji

Kliknij ten przycisk, aby wyświetlić plik kodu zdarzeń, w `Startup` `Shutdown`którym `UnhandledException` `StartupNextInstance` można `NetworkAvailabilityChanged`zapisywać zdarzenia dla zdarzeń struktury aplikacji , i . Można również zastąpić niektóre metody struktury aplikacji. Na przykład można zmienić zachowanie wyświetlania ekranu powitalnego, zastępując `OnInitialize`.

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>Właściwości struktury aplikacji systemu Windows dla aplikacji Windows Presentation Foundation (WPF)

Następujące ustawienia są dostępne w sekcji **właściwości struktury aplikacji systemu Windows,** gdy projekt jest aplikacją Windows Presentation Foundation (WPF). Te opcje są dostępne tylko wtedy, gdy zaznaczone jest pole wyboru **Włącz strukturę aplikacji.** Opcje wymienione w tej tabeli są dostępne tylko dla aplikacji przeglądarki WPF lub WPF. Nie są one dostępne dla bibliotek WPF User Control lub Custom Control.

### <a name="shutdown-mode"></a>Tryb wyłączania

Ta właściwość ma zastosowanie tylko do aplikacji Windows Presentation Foundation (WPF).

Wybierz **opcję Jawne zamykanie,** aby określić, że aplikacja kończy działanie podczas jawnego wywoływania <xref:System.Windows.Application.Shutdown%2A>.

Wybierz **na ostatnie okno blisko,** aby określić, że aplikacja kończy <xref:System.Windows.Application.Shutdown%2A>się po zamknięciu ostatniego okna lub podczas jawnego wywołania . Jest to ustawienie domyślne.

Wybierz **w oknie głównym blisko,** aby określić, że zamknięcie aplikacji <xref:System.Windows.Application.Shutdown%2A>po zamknięciu okna głównego lub jawnie wywołać .

Aby uzyskać więcej informacji na temat korzystania z tego ustawienia, zobacz<xref:System.Windows.Application.Shutdown%2A>

### <a name="edit-xaml"></a>Edytuj kod XAML

Ten przycisk otwiera plik definicji aplikacji (Application.xaml) w edytorze XAML. Po kliknięciu tego przycisku *plik Application.xaml* zostanie otwarty w węźle definicji aplikacji. Może być konieczne edytowanie tego pliku w celu wykonania określonych zadań, takich jak definiowanie zasobów. Jeśli plik definicji aplikacji nie istnieje, projektant projektu tworzy jeden.

### <a name="view-application-events"></a>Wyświetlanie zdarzeń aplikacji

Ten przycisk `Application` otwiera plik klasy (*Application.xaml.vb*) w edytorze kodu. Jeśli plik nie istnieje, projektant projektu tworzy jeden z odpowiednią nazwą klasy i obszaru nazw.

Obiekt <xref:System.Windows.Application> wywołuje zdarzenia, gdy wystąpią pewne zmiany stanu aplikacji (na przykład podczas uruchamiania lub zamykania aplikacji). Aby uzyskać pełną listę zdarzeń, które ta <xref:System.Windows.Application>klasa udostępnia, zobacz . Te zdarzenia są obsługiwane w sekcji `Application` kodu użytkownika klasy częściowej.
