---
title: Strona aplikacji we właściwościach projektu VB
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesApplicationWPF
- vb.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84874328c2f7a20a79370ff210eb51d966ec4648
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355205"
---
# <a name="application-page-project-designer-visual-basic"></a>Strona aplikacji, Projektant projektu (Visual Basic)

Użyj **aplikacji** strony projektanta projektu, aby określić ustawienia aplikacji i właściwości projektu.

Aby uzyskać dostęp do **aplikacji** wybierz węzeł projektu (nie **rozwiązania** węźle) w **Eksploratora rozwiązań**. Następnie wybierz **projektu** > **właściwości** na pasku menu. Gdy **projektanta projektu** pojawi się, wybierz **aplikacji** kartę.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Ustawienia ogólne aplikacji

Poniższe opcje umożliwiają konfigurowanie ogólnych ustawień dla aplikacji.

### <a name="assembly-name"></a>Nazwa zestawu

Określa nazwę pliku wyjściowego, który zawiera manifest zestawu. Jeśli zmienisz tę właściwość **Nazwa wyjściowego** zmienia także właściwości.

Można również określić nazwę pliku wyjściowego z poziomu wiersza polecenia przy użyciu [/out (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/out) przełącznika kompilatora.

Aby dowiedzieć się, jak programowo dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

### <a name="root-namespace"></a>Główna przestrzeń nazw

Określa podstawowej przestrzeni nazw dla wszystkich plików w projekcie. Na przykład jeśli ustawisz **Namespace głównego** do `Project1` i masz `Class1` poza dowolnego obszaru nazw w kodzie będzie jego przestrzeń nazw `Project1.Class1`. Jeśli masz `Class2` w przestrzeni nazw `Order` w kodzie, będzie jego przestrzeń nazw `Project1.Order.Class2`.

Jeśli wyczyścisz **Namespace głównego**, struktura przestrzeni nazw projektu można określić w kodzie.

> [!NOTE]
> Jeśli używasz `Global` — słowo kluczowe w [Namespace, instrukcja](/dotnet/visual-basic/language-reference/statements/namespace-statement), można zdefiniować przestrzeni nazw poza głównej przestrzeni nazw projektu. Jeśli wyczyścisz **Namespace głównego**, `Global` staje się przestrzeń nazw najwyższego poziomu, co eliminuje potrzebę `Global` — słowo kluczowe w `Namespace` instrukcji. Aby uzyskać więcej informacji, zobacz "Globalne — słowo kluczowe w Namespace instrukcji" w [przestrzeni nazw w języku Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces).

Aby uzyskać informacje o sposobie tworzenia przestrzeni nazw w kodzie, zobacz [Namespace, instrukcja](/dotnet/visual-basic/language-reference/statements/namespace-statement).

Aby uzyskać więcej informacji na temat właściwości przestrzeń nazw głównego zobacz [/rootnamespace —](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace).

Aby dowiedzieć się, jak programowo dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

### <a name="target-framework-all-configurations"></a>Platforma docelowa (wszystkie konfiguracje)

Określa wersję programu .NET Framework, cele aplikacji. Ta opcja może mieć różne wartości w zależności od tego, które wersje programu .NET Framework są zainstalowane na tym komputerze.

Wartość domyślna jest zgodna platformę docelową, które zostały określone podczas tworzenia projektu.

> [!NOTE]
> Wstępnie wymagane pakiety, które są wymienione w [wstępnie wymagane składniki, okno dialogowe](../../ide/reference/prerequisites-dialog-box.md) są ustawiane automatycznie po otwarciu okna dialogowego po raz pierwszy. Jeśli użytkownik zmieni później platformę docelową projektu, należy określić wstępnie wymagane składniki ręcznie, aby dopasować do nowej platformy docelowej.

Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) i [programu Visual Studio Wielowersyjnością kodu – Przegląd](../../ide/visual-studio-multi-targeting-overview.md).

### <a name="application-type"></a>Typ aplikacji

Określa typ aplikacji pozwalają na tworzenie. Wartości są różne w zależności od typu projektu. Na przykład w przypadku **Windows Forms App** projektu, można określić **aplikacja interfejsu Windows Forms**, **biblioteki klas**, **aplikację Konsolową**, **Usługi Windows**, lub **Biblioteka formantów sieci Web**.

W przypadku projektu aplikacji sieci web, należy określić **biblioteki klas**.

Aby uzyskać więcej informacji na temat **typ aplikacji** właściwości, zobacz [/TARGET (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/target). Aby uzyskać informacje o tym, jak programowo uzyskać dostęp właściwości do, zobacz <xref:VSLangProj.ProjectProperties.OutputType%2A>.

### <a name="auto-generate-binding-redirects"></a>Automatyczne generowanie przekierowania powiązań

Przekierowania powiązań są dodawane do projektu, jeśli Twoja aplikacja lub jej składniki odwołują się do więcej niż jednej wersji tego samego zestawu. Jeśli chcesz ręcznie definiować przekierowania powiązań w pliku projektu, usuń zaznaczenie opcji **automatycznego generowania przekierowania powiązań**.

Aby uzyskać więcej informacji o przekierowywaniu, zobacz [przekierowanie wersji zestawu](/dotnet/framework/configure-apps/redirect-assembly-versions).

### <a name="startup-form--startup-object--startup-uri"></a>Formularz początkowy / obiekt początkowy / startowy identyfikator URI

Określa punkt startowy aplikacji formularza lub wpis.

Jeśli **struktury aplikacji Włącz** jest zaznaczone (ustawienie domyślne), ta lista jest zatytułowana **formularz początkowy** i pokazuje tylko formularze, ponieważ struktura aplikacji obsługuje tylko formularze uruchamiania nie obiektów.

Jeśli projekt jest aplikacją przeglądarki środowiska WPF, ta lista jest zatytułowana **startowy identyfikator URI**, a wartość domyślna to **Page1.xaml**. **Startowy identyfikator URI** listy pozwala na określenie zasobu interfejsu użytkownika (a XAML element), który aplikacja wyświetla podczas uruchamiania aplikacji. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Application.StartupUri%2A>.

Jeśli **struktury aplikacji Włącz** jest wyczyszczone, ta lista staje się **obiekt początkowy** i pokazuje formularze i klas lub moduły z `Sub Main`.

**Obiekt początkowy** definiuje punkt wejścia, który ma być wywoływana podczas ładowania aplikacji. Zazwyczaj ta opcja jest ustawiona na formularzu głównym w aplikacji lub do `Sub Main` procedury, które należy uruchamiać podczas uruchamiania aplikacji. Ponieważ biblioteki klas nie ma punktu wejścia, ich jedyną opcją dla tej właściwości jest **(Brak)**. Aby uzyskać więcej informacji, zobacz [/main](/dotnet/visual-basic/reference/command-line-compiler/main). Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

### <a name="icon"></a>Ikona

Określa plik .ico, który ma być używany jako ikona programu. Wybierz  **\<Przeglądaj … >** aby przejść do istniejącej grafiki. Zobacz [/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) (lub [/win32icon (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)) Aby uzyskać więcej informacji. Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

### <a name="assembly-information"></a>Informacje o zestawie

Kliknij ten przycisk, aby wyświetlić [informacje o zestawie — okno dialogowe](../../ide/reference/assembly-information-dialog-box.md).

### <a name="enable-application-framework"></a>Włącz struktury aplikacji

Określa, czy projekt będzie używać struktury aplikacji. Ustawienie tej opcji ma wpływ na opcje dostępne w **formularz początkowy**/**obiekt początkowy**.

Jeśli to pole wyboru jest zaznaczone, aplikacja używa standardowych `Sub Main`. Zaznaczenie tego pola wyboru włącza funkcje **właściwości szablonu aplikacji Windows** sekcji, a także wymaga wybrania formularz początkowy.

Jeśli to pole wyboru jest wyczyszczone, aplikacja używa niestandardowej `Sub Main` ustawionego w **formularz początkowy**. W takim przypadku można określić obiekt początkowy (niestandardowego `Sub Main` w metodzie lub klasie) lub formularz. Ponadto opcje w **właściwości szablonu aplikacji Windows** sekcji staną się niedostępne.

### <a name="view-windows-settings"></a>Wyświetl ustawienia Windows

Kliknij ten przycisk, aby wygenerować i otworzyć *app.manifest* pliku. Visual Studio używa tego pliku do generowania manifestu dane aplikacji. A następnie ustaw kontroli konta użytkownika żądany poziom wykonywania, modyfikując `<requestedExecutionLevel>` tagów w *app.manifest* w następujący sposób:

`<requestedExecutionLevel level="asInvoker" />`

ClickOnce działa z poziomem `asInvoker` lub w trybie zwirtualizowanych (nie generowania manifestu). Aby określić tryb zwirtualizowanych, usuń cały tag z app.manifest.

Aby uzyskać więcej informacji na temat generowania manifestu, zobacz [wdrażania ClickOnce w systemie Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).

## <a name="windows-application-framework-properties"></a>Właściwości szablonu aplikacji Windows

Następujące ustawienia są dostępne w **właściwości szablonu aplikacji Windows** sekcji. Te opcje są dostępne tylko wtedy, gdy **struktury aplikacji Włącz** pole wyboru jest zaznaczone.

> [!TIP]
> Opis sekcji następujące po niej **właściwości szablonu aplikacji Windows** ustawienia specyficzne dla aplikacji Windows Presentation Foundation (WPF).

### <a name="enable-xp-visual-styles"></a>Włączyć style wizualne XP

Włącza lub wyłącza stylów wizualnych Windows XP, znany także jako *Windows XP motywy*. Na przykład stylów wizualnych Windows XP włącz kontrolek z zaokrąglone rogi i dynamiczne kolorów. Wartość domyślna jest ustawiona.

### <a name="make-single-instance-application"></a>Pojedyncze wystąpienie aplikacji

Zaznacz to pole wyboru, aby uniemożliwić użytkownikom uruchamianie wielu wystąpień aplikacji. Domyślnym ustawieniem jest to pole wyboru *wyczyszczone*, która zezwala na wiele wystąpień aplikacji do uruchomienia. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> zdarzeń.

### <a name="save-mysettings-on-shutdown"></a>Zapisz My.Settings podczas zamykania

Zaznacz to pole wyboru, aby określić, że aplikacja `My.Settings` ustawienia są zapisywane, gdy użytkownicy wyłączają komputery. Ustawieniem domyślnym jest włączona. Jeśli ta opcja jest wyłączona, można zapisać ustawień aplikacji ręcznie, wywołując `My.Settings.Save`.

### <a name="authentication-mode"></a>Tryb uwierzytelniania

Wybierz **Windows** (ustawienie domyślne) do określenia korzystanie z uwierzytelniania Windows, aby zidentyfikować obecnie zalogowanego użytkownika. Te informacje w czasie wykonywania można pobrać za pomocą `My.User` obiektu. Wybierz **zdefiniowanych przez aplikację** jeśli zapewni kodu do uwierzytelniania kont użytkowników zamiast domyślnych metod uwierzytelniania Windows.

### <a name="shutdown-mode"></a>Tryb zamykania

Wybierz **podczas uruchamiania formularz zostanie zamknięty** (ustawienie domyślne) do określenia, że zamknięcie aplikacji, gdy formularz jest ustawiona jako formularz początkowy jest zamykane, nawet jeśli inne formy są otwarte. Wybierz **podczas ostatniego formularz zostanie zamknięty** do określenia, czy podczas ostatniego formularza jest zamknięty lub zakończyć działanie aplikacji `My.Application.Exit` lub `End` jest nazwana jawnie.

Wybierz **podczas zamykania jawne** do określenia, czy zakończyć działanie aplikacji, gdy jawnie wywołać `Shutdown`.

Wybierz **na ostatnim oknie Zamknij** Aby określić, gdy ostatnie okno zostanie zamknięte lub gdy jawnie wywołać zakończyć działanie aplikacji `Shutdown`. To jest ustawienie domyślne.

Wybierz **w głównym oknie, Zamknij** do określenia, czy zakończyć działanie aplikacji, po zamknięciu okna głównego, lub gdy jawnie wywołać `Shutdown`.

### <a name="splash-screen"></a>Ekran powitalny

Wybierz formularz, który ma być używany jako ekran powitalny. Musisz wcześniej utworzono ekran powitalny za pomocą formularza lub szablonu. Wartość domyślna to **(Brak)**.

### <a name="view-application-events"></a>Wyświetl zdarzenia aplikacji

Kliknij ten przycisk, aby wyświetlić plik kodu zdarzenia, w którym można zapisać zdarzeń dla zdarzeń aplikacji w ramach `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` i `NetworkAvailabilityChanged`. Można również zastąpić niektóre metody w ramach aplikacji. Na przykład można zmienić zachowanie wyświetlania na ekranie powitalnym przez zastąpienie `OnInitialize`.

## <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-apps"></a>Właściwości szablonu aplikacji Windows dla aplikacji Windows Presentation Foundation (WPF)

Następujące ustawienia są dostępne w **właściwości szablonu aplikacji Windows** sekcji, gdy projekt jest aplikacją Windows Presentation Foundation (WPF). Te opcje są dostępne tylko wtedy, gdy **struktury aplikacji Włącz** pole wyboru jest zaznaczone. Opcje wymienione w poniższej tabeli są dostępne tylko w przypadku WPF lub WPF aplikacji przeglądarki. Nie są one dostępne dla bibliotek formanty użytkownika WPF lub formant niestandardowy.

### <a name="shutdown-mode"></a>Tryb zamykania

Ta właściwość ma zastosowanie tylko do aplikacji Windows Presentation Foundation (WPF).

Wybierz **podczas zamykania jawne** do określenia, czy zakończyć działanie aplikacji, gdy jawnie wywołać <xref:System.Windows.Application.Shutdown%2A>.

Wybierz **na ostatnim oknie Zamknij** Aby określić, gdy ostatnie okno zostanie zamknięte lub gdy jawnie wywołać zakończyć działanie aplikacji <xref:System.Windows.Application.Shutdown%2A>. To jest ustawienie domyślne.

Wybierz **w głównym oknie, Zamknij** do określenia, czy zakończyć działanie aplikacji, po zamknięciu okna głównego, lub gdy jawnie wywołać <xref:System.Windows.Application.Shutdown%2A>.

Aby uzyskać więcej informacji na temat używania tego ustawienia Zobacz <xref:System.Windows.Application.Shutdown%2A>

### <a name="edit-xaml"></a>Edytuj XAML

Ten przycisk otwiera plik definicji aplikacji (Application.xaml) w edytorze XAML. Po kliknięciu tego przycisku *Application.xaml* otwiera się w węźle definicji aplikacji. Trzeba edytować ten plik do wykonania niektórych zadań, takich jak definiowanie zasobów. Jeśli nie ma pliku definicji aplikacji, Projektant projektu tworzony jest jeden.

### <a name="view-application-events"></a>Wyświetl zdarzenia aplikacji

Ten przycisk otwiera `Application` plik klasy (*Application.xaml.vb*) w edytorze kodu. Jeśli plik nie istnieje, Projektant projektu tworzony jest jeden z odpowiednią nazwę klasy i przestrzeni nazw.

<xref:System.Windows.Application> Obiektu wywołuje zdarzenia po wprowadzeniu pewnych zmian stanu aplikacji (np. na uruchamianie aplikacji lub zamknięcie). Aby uzyskać pełną listę zdarzeń, które udostępnia tę klasę, zobacz <xref:System.Windows.Application>. Zdarzenia te są obsługiwane w sekcji kodu użytkownika `Application` klasy częściowej.