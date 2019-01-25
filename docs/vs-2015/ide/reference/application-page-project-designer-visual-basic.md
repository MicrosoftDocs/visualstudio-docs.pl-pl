---
title: Strona aplikacji, Projektant (Visual Basic) projektu | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 21f94323fbfa7369e3fef93b0f95a8db2ea46ce2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774863"
---
# <a name="application-page-project-designer-visual-basic"></a>Strona aplikacji, Projektant projektu (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Użyj **aplikacji** strony projektanta projektu, aby określić ustawienia aplikacji i właściwości projektu.  
  
 Aby uzyskać dostęp do **aplikacji** wybierz węzeł projektu (nie **rozwiązania** węźle) w **Eksploratora rozwiązań**. Następnie wybierz **projektu**, **właściwości** na pasku menu. Gdy pojawi się w Projektancie projektu, kliknij przycisk **aplikacji** kartę.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="general-application-settings"></a>Ustawienia ogólne aplikacji  
 Poniższe opcje umożliwiają konfigurowanie ogólnych ustawień dla aplikacji.  
  
 **Nazwa zestawu**  
 Określa nazwę pliku wyjściowego, który zawiera manifest zestawu. Jeśli zmienisz tę właściwość **Nazwa wyjściowego** zmienią właściwości. Ta zmiana może wprowadzić polecenie w wierszu polecenia, za pomocą [/out (Visual Basic)](http://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae). Aby dowiedzieć się, jak programowo dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.  
  
 **Główna przestrzeń nazw**  
 Określa podstawowej przestrzeni nazw dla wszystkich plików w projekcie. Na przykład jeśli ustawisz **Namespace głównego** do `Project1` i masz `Class1` poza dowolnego obszaru nazw w kodzie będzie jego przestrzeń nazw `Project1.Class1`. Jeśli masz `Class2` w przestrzeni nazw `Order` w kodzie, będzie jego przestrzeń nazw `Project1.Order.Class2`.  
  
 Jeśli wyczyścisz **Namespace głównego**, struktura przestrzeni nazw projektu można określić w kodzie.  
  
> [!NOTE]
>  Jeśli używasz Global — słowo kluczowe w [Namespace, instrukcja](http://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2), można zdefiniować przestrzeni nazw poza głównej przestrzeni nazw projektu. Jeśli wyczyścisz **Namespace głównego**, `Global` staje się przestrzeń nazw najwyższego poziomu, co eliminuje potrzebę `Global` — słowo kluczowe w `Namespace` instrukcji. Aby uzyskać więcej informacji, zobacz "Globalne — słowo kluczowe w Namespace instrukcji" w [przestrzeni nazw w języku Visual Basic](http://msdn.microsoft.com/library/cffac744-ab8c-4f1f-ba50-732c22ab4b88).  
  
 Aby uzyskać informacje o sposobie tworzenia przestrzeni nazw w kodzie, zobacz [Namespace, instrukcja](http://msdn.microsoft.com/library/a31fbd95-9ace-4c3d-bbb1-51222a2272b2).  
  
 Aby uzyskać więcej informacji na temat właściwości przestrzeń nazw głównego zobacz [/rootnamespace —](http://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783).  
  
 Aby dowiedzieć się, jak programowo dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.  
  
 **Platforma docelowa (wszystkie konfiguracje)**  
 Określa wersję programu .NET Framework, cele aplikacji. Ta opcja może mieć różne wartości w zależności od tego, które wersje programu .NET Framework są zainstalowane na tym komputerze.  
  
 Wartość domyślna jest zgodna platformy docelowej, określone w **nowy projekt** okno dialogowe.  
  
> [!NOTE]
>  Wstępnie wymagane pakiety, które są wymienione w [wstępnie wymagane składniki, okno dialogowe](../../ide/reference/prerequisites-dialog-box.md) są ustawiane automatycznie po otwarciu okna dialogowego po raz pierwszy. Jeśli użytkownik zmieni później platformę docelową projektu, należy określić wstępnie wymagane składniki ręcznie, aby dopasować do nowej platformy docelowej.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) i [programu Visual Studio Wielowersyjnością kodu – Przegląd](../../ide/visual-studio-multi-targeting-overview.md).  
  
 **Typ aplikacji**  
 Określa typ aplikacji pozwalają na tworzenie. Aby uzyskać [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikacji, można określić **Windows Store App**, **biblioteki klas**, lub **plik WinMD**. W przypadku większości innych typów aplikacji, możesz określić **aplikacji Windows**, **aplikację Konsolową**, **biblioteki klas**, **usługi Windows**, lub **Biblioteka formantów sieci Web**.  
  
 W przypadku projektu aplikacji sieci web, należy określić **biblioteki klas**.  
  
 Jeśli określisz **plik WinMD** opcji typów może zostać przedstawione dowolnego środowiska wykonawczego Windows, język programowania. Przez funkcję tworzenia pakietów danych wyjściowych projektu jako plik WinMD, kod aplikacji w wielu językach i współdziałania tak, jakby jego autorem kod w języku. Możesz użyć **plik WinMD** dotycząca rozwiązania przeznaczone dla bibliotek środowiska wykonawczego Windows, w tym [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [Tworzenie składników środowiska wykonawczego Windows w języku C# i Visual Basic](http://go.microsoft.com/fwlink/?LinkId=231895).  
  
> [!NOTE]
>  Środowisko wykonawcze Windows można typów projektów, aby były wyświetlane jako obiektów natywnych w jakikolwiek język są one używane. Na przykład JavaScript aplikacji współdziałających ze środowiska wykonawczego Windows ich używać jako zbiór obiektów JavaScript i aplikacji w języku C# korzystanie z biblioteki jako kolekcję obiektów platformy .NET. Upakowanie danych wyjściowych projektu w formacie pliku WinMD, możesz korzystać z zalet tej samej technologii, która używa środowiska wykonawczego Windows.  
  
 Aby uzyskać więcej informacji na temat **typ aplikacji** właściwości, zobacz [/TARGET (Visual Basic)](http://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c). Aby uzyskać informacje o tym, jak programowo uzyskać dostęp właściwości do, zobacz <xref:VSLangProj.ProjectProperties.OutputType%2A>.  
  
 **Ikona**  
 Określa plik .ico, który ma być używany jako ikona programu. Wybierz  **\<Przeglądaj … >** aby przejść do istniejącej grafiki. Zobacz [/win32icon](http://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) (lub [/win32icon (opcje kompilatora C#)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138)) Aby uzyskać więcej informacji. Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.  
  
 **Formularz początkowy / obiekt początkowy / startowy identyfikator URI**  
 Określa punkt startowy aplikacji formularza lub wpis.  
  
 Jeśli **struktury aplikacji Włącz** jest zaznaczone (ustawienie domyślne), ta lista jest zatytułowana **formularz początkowy** i pokazuje tylko formularze, ponieważ struktura aplikacji obsługuje tylko formularze uruchamiania nie obiektów.  
  
 Jeśli projekt jest aplikacją przeglądarki środowiska WPF, ta lista jest zatytułowana **startowy identyfikator URI**, a wartość domyślna to **Page1.xaml**. **Startowy identyfikator URI** listy pozwala na określenie zasobu interfejsu użytkownika (a XAML element), który aplikacja wyświetla podczas uruchamiania aplikacji. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Application.StartupUri%2A>.  
  
 Jeśli **struktury aplikacji Włącz** jest wyczyszczone, ta lista staje się **obiekt początkowy** i pokazuje formularze i klas lub moduły z `Sub Main`.  
  
 **Obiekt początkowy** definiuje punkt wejścia, który ma być wywoływana podczas ładowania aplikacji. Zazwyczaj ta opcja jest ustawiona na formularzu głównym w aplikacji lub do `Sub Main` procedury, które należy uruchamiać podczas uruchamiania aplikacji. Ponieważ biblioteki klas nie ma punktu wejścia, ich jedyną opcją dla tej właściwości jest **(Brak)**. Aby uzyskać więcej informacji, zobacz [/main](http://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0). Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.StartupObject%2A>.  
  
 **Informacje o zestawie**  
 Kliknij ten przycisk, aby wyświetlić [informacje o zestawie — okno dialogowe](../../ide/reference/assembly-information-dialog-box.md).  
  
 **Włącz struktury aplikacji**  
 Określa, czy projekt będzie używać struktury aplikacji. Ustawienie tej opcji ma wpływ na opcje dostępne w **formularz początkowy**/**obiekt początkowy**.  
  
 Jeśli to pole wyboru jest zaznaczone, aplikacja używa standardowych `Sub Main`. Zaznaczenie tego pola wyboru włącza funkcje **właściwości szablonu aplikacji Windows** sekcji, a także wymaga wybrania formularz początkowy.  
  
 Jeśli to pole wyboru jest wyczyszczone, aplikacja używa niestandardowej `Sub Main` ustawionego w **formularz początkowy**. W takim przypadku można określić obiekt początkowy (niestandardowego `Sub Main` w metodzie lub klasie) lub formularz. Ponadto opcje w **właściwości szablonu aplikacji Windows** sekcji staną się niedostępne.  
  
 **Wyświetl ustawienia Windows**  
 Kliknij ten przycisk, aby wygenerować i Otwórz plik app.manifest. Visual Studio używa tego pliku do generowania manifestu dane aplikacji. A następnie ustaw kontroli konta użytkownika żądany poziom wykonywania, modyfikując `<requestedExecutionLevel>` tagów w app.manifest w następujący sposób:  
  
 `<requestedExecutionLevel level="asInvoker" />`  
  
 ClickOnce działa z poziomem `asInvoker` lub w trybie zwirtualizowanych (nie generowania manifestu). Aby określić tryb zwirtualizowanych, usuń cały tag z app.manifest.  
  
 Aby uzyskać więcej informacji na temat generowania manifestu, zobacz [wdrażania ClickOnce w systemie Windows Vista](../../deployment/clickonce-deployment-on-windows-vista.md).  
  
## <a name="windows-application-framework-properties"></a>Właściwości szablonu aplikacji Windows  
 Następujące ustawienia są dostępne w **właściwości szablonu aplikacji Windows** sekcji. Te opcje są dostępne tylko wtedy, gdy **struktury aplikacji Włącz** pole wyboru jest zaznaczone. Opis sekcji następujące po niej **właściwości szablonu aplikacji Windows** ustawienia dla aplikacji Windows Presentation Foundation (WPF).  
  
 **Włączyć style wizualne XP**  
 Włącza lub wyłącza stylów wizualnych Windows XP, znany także jako *Windows XP motywy*. Na przykład stylów wizualnych Windows XP włącz kontrolek z zaokrąglone rogi i dynamiczne kolorów. Wartość domyślna jest ustawiona. Aby uzyskać więcej informacji na temat funkcji stylów wizualnych Windows XP zobacz [funkcje systemu Windows XP i kontrolki formularzy Windows](http://msdn.microsoft.com/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)).  
  
 **Pojedyncze wystąpienie aplikacji**  
 Zaznacz to pole wyboru, aby uniemożliwić użytkownikom uruchamianie wielu wystąpień aplikacji. Ustawieniem domyślnym dla tego pola wyboru jest wyczyszczone. To ustawienie zezwala na wiele wystąpień aplikacji do uruchomienia.  
  
 **Zapisz My.Settings podczas zamykania**  
 Zaznacz to pole wyboru, aby określić, że aplikacja `My.Settings` ustawienia są zapisywane, gdy użytkownicy wyłączają komputery. Ustawieniem domyślnym jest włączona. Jeśli ta opcja jest wyłączona, można zapisać ustawień aplikacji ręcznie, wywołując `My.Settings.Save`.  
  
 **Tryb uwierzytelniania**  
 Wybierz **Windows** (ustawienie domyślne) do określenia korzystanie z uwierzytelniania Windows, aby zidentyfikować obecnie zalogowanego użytkownika. Te informacje w czasie wykonywania można pobrać za pomocą `My.User` obiektu. Wybierz **zdefiniowanych przez aplikację** jeśli zapewni kodu do uwierzytelniania kont użytkowników zamiast domyślnych metod uwierzytelniania Windows.  
  
 **Tryb zamykania**  
 Wybierz **podczas uruchamiania formularz zostanie zamknięty** (ustawienie domyślne) do określenia, że zamknięcie aplikacji, gdy formularz jest ustawiona jako formularz początkowy jest zamykane, nawet jeśli inne formy są otwarte. Wybierz **podczas ostatniego formularz zostanie zamknięty** do określenia, czy podczas ostatniego formularza jest zamknięty lub zakończyć działanie aplikacji `My.Application.Exit` lub `End` jest nazwana jawnie.  
  
 Wybierz **podczas zamykania jawne** do określenia, czy zakończyć działanie aplikacji, gdy jawnie wywołać `Shutdown`.  
  
 Wybierz **na ostatnim oknie Zamknij** Aby określić, gdy ostatnie okno zostanie zamknięte lub gdy jawnie wywołać zakończyć działanie aplikacji `Shutdown`. To jest ustawienie domyślne.  
  
 Wybierz **w głównym oknie, Zamknij** do określenia, czy zakończyć działanie aplikacji, po zamknięciu okna głównego, lub gdy jawnie wywołać `Shutdown`.  
  
 **Ekran powitalny**  
 Wybierz formularz, który ma być używany jako ekran powitalny. Musisz wcześniej utworzono ekran powitalny za pomocą formularza lub szablonu. Wartość domyślna to **(Brak)**.  
  
 **Wyświetl zdarzenia aplikacji**  
 Kliknij ten przycisk, aby wyświetlić plik kodu zdarzenia, w którym można zapisać zdarzeń dla zdarzeń aplikacji w ramach `Startup`, `Shutdown`, `UnhandledException`, `StartupNextInstance` i `NetworkAvailabilityChanged`. Można również zastąpić niektóre metody w ramach aplikacji. Na przykład można zmienić zachowanie wyświetlania na ekranie powitalnym przez zastąpienie `OnInitialize`.  
  
### <a name="windows-application-framework-properties-for-windows-presentation-foundation-wpf-applications"></a>Właściwości szablonu aplikacji Windows dla aplikacji programu Windows Presentation Foundation (WPF)  
 Następujące ustawienia są dostępne w **właściwości szablonu aplikacji Windows** sekcji, gdy projekt jest aplikacją programu Windows Presentation Foundation. Te opcje są dostępne tylko wtedy, gdy **struktury aplikacji Włącz** pole wyboru jest zaznaczone. Opcje wymienione w poniższej tabeli są dostępne tylko w przypadku aplikacji WPF lub aplikacje przeglądarki WPF. Nie są one dostępne dla bibliotek formanty użytkownika WPF lub formant niestandardowy.  
  
 **Tryb zamykania**  
 Ta właściwość ma zastosowanie tylko do aplikacji Windows Presentation Foundation.  
  
 Wybierz **podczas zamykania jawne** do określenia, czy zakończyć działanie aplikacji, gdy jawnie wywołać <xref:System.Windows.Application.Shutdown%2A>.  
  
 Wybierz **na ostatnim oknie Zamknij** Aby określić, gdy ostatnie okno zostanie zamknięte lub gdy jawnie wywołać zakończyć działanie aplikacji <xref:System.Windows.Application.Shutdown%2A>. To jest ustawienie domyślne.  
  
 Wybierz **w głównym oknie, Zamknij** do określenia, czy zakończyć działanie aplikacji, po zamknięciu okna głównego, lub gdy jawnie wywołać <xref:System.Windows.Application.Shutdown%2A>.  
  
 Aby uzyskać więcej informacji na temat używania tego ustawienia Zobacz <xref:System.Windows.Application.Shutdown%2A>  
  
 **Edytuj XAML**  
 Kliknij ten przycisk, aby otworzyć i zmodyfikować plik definicji aplikacji (Application.xaml) w edytorze XAML. Po kliknięciu tego przycisku, Application.xaml otwiera się w węźle definicji aplikacji. Trzeba edytować ten plik do wykonania niektórych zadań, takich jak definiowanie zasobów. Jeśli nie ma pliku definicji aplikacji, Projektant projektu tworzony jest jeden.  
  
 **Wyświetl zdarzenia aplikacji**  
 Kliknij ten przycisk, aby wyświetlić `Application` plik klasy częściowe (Application.xaml.vb) w edytorze kodu. Jeśli plik nie istnieje, Projektant projektu tworzony jest jeden z odpowiednią nazwę klasy i przestrzeni nazw.  
  
 <xref:System.Windows.Application> Obiektu wywołuje zdarzenia po wprowadzeniu pewnych zmian stanu aplikacji (np. na uruchamianie aplikacji lub zamknięcie). Aby uzyskać pełną listę zdarzeń, które udostępnia tę klasę, zobacz <xref:System.Windows.Application>. Zdarzenia te są obsługiwane w sekcji kodu użytkownika `Application` klasy częściowej.  
  
## <a name="see-also"></a>Zobacz też  
[Zarządzanie właściwościami aplikacji](../../ide/application-properties.md) [pisany w rozwiązaniach pakietu Office](http://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)
