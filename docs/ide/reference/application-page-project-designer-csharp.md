---
title: Strony aplikacji C# właściwości projektu
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f287de1e756d20575e1c72775719b2c366534b6d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927558"
---
# <a name="application-page-project-designer-c"></a>Strona aplikacji, Projektant projektu (C#)

Użyj **aplikacji** strony **projektanta projektu** do określania ustawień aplikacji i właściwości projektu.

Aby uzyskać dostęp do **aplikacji** wybierz węzeł projektu (nie **rozwiązania** węźle) w **Eksploratora rozwiązań**. Następnie wybierz **projektu** > **właściwości** na pasku menu. Podczas **projektanta projektu** zostanie wyświetlona, kliknij przycisk **aplikacji** kartę.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Ustawienia ogólne aplikacji

Poniższe opcje umożliwiają konfigurowanie ogólnych ustawień dla aplikacji.

**Nazwa zestawu**

Określa nazwę pliku wyjściowego, który będzie przechowywać manifest zestawu. Zmiana tej właściwości powoduje również **Nazwa wyjściowego** właściwości.

Można również wprowadzenie tej zmiany z wiersza polecenia przy użyciu [/out (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).

Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Domyślna przestrzeń nazw**

Określa podstawowej przestrzeni nazw dla plików dodawane do projektu.

Zobacz [przestrzeni nazw](/dotnet/csharp/language-reference/keywords/namespace) Aby uzyskać więcej informacji na temat tworzenia przestrzeni nazw w kodzie.

Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Struktura docelowa**

Określa wersję programu .NET Framework, cele aplikacji. Ta opcja może mieć różne wartości w zależności od tego, które wersje programu .NET Framework są zainstalowane na tym komputerze.

Domyślnie wartość jest taka sama jak platforma docelowa, które wybrano w **nowy projekt** okno dialogowe.

> [!NOTE]
> Wstępnie wymagane pakiety wymienione w [wstępnie wymagane składniki, okno dialogowe](../../ide/reference/prerequisites-dialog-box.md) są ustawiane automatycznie przy pierwszym otwarciu okna dialogowego. Jeśli użytkownik zmieni później platformę docelową projektu, musisz wybrać wstępnie wymagane składniki ręcznie, aby dopasować do nowej platformy docelowej.

Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) i [programu Visual Studio Wielowersyjnością kodu – Przegląd](../../ide/visual-studio-multi-targeting-overview.md).

**Typ danych wyjściowych**

Określa typ aplikacji pozwalają na tworzenie. Wartości są różne w zależności od typu projektu. Na przykład w przypadku **aplikacja Konsolowa** projektu, można określić **aplikacji Windows**, **aplikację Konsolową**, lub **biblioteki klas** jako Typ danych wyjściowych.

W przypadku projektu aplikacji sieci web, należy określić **biblioteki klas**.

Aby uzyskać więcej informacji na temat **typ danych wyjściowych** właściwości, zobacz [/target (C# opcje kompilatora)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).

Aby dowiedzieć się, jak programowo dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.OutputType%2A>.

**Automatyczne generowanie przekierowania powiązań**

Przekierowania powiązań są dodawane do projektu, jeśli Twoja aplikacja lub jej składniki odwołują się do więcej niż jednej wersji tego samego zestawu. Jeśli chcesz ręcznie definiować przekierowania powiązań w pliku projektu, usuń zaznaczenie opcji **automatycznego generowania przekierowania powiązań**. To pole wyboru została wprowadzona w programie Visual Studio 2017 wersji 15.7.

Aby uzyskać więcej informacji o przekierowywaniu, zobacz [przekierowanie wersji zestawu](/dotnet/framework/configure-apps/redirect-assembly-versions).

**Obiekt początkowy**

Definiuje punkt wejścia, który ma być wywoływana podczas ładowania aplikacji. Zazwyczaj jest ono ustawione w formularzu głównym w aplikacji lub do `Main` procedury, które należy uruchamiać podczas uruchamiania aplikacji. Ponieważ biblioteki klas nie ma punktu wejścia, ich jedyną opcją dla tej właściwości jest **(nie ustawiono)**.

Domyślnie w projekcie aplikacji WPF, ta opcja jest ustawiona na **(nie ustawiono)**. Druga opcja to \[nazwa_projektu] .App. W projekcie WPF należy ustawić startowy identyfikator URI do ładowania zasobów interfejsu użytkownika podczas uruchamiania aplikacji. Aby to zrobić, otwórz *Application.xaml* pliku w projekcie i ustaw `StartupUri` właściwości *.xaml* pliku w projekcie, takie jak *Window1.xaml*. Aby uzyskać listę elementów głównych dopuszczalne, zobacz <xref:System.Windows.Application.StartupUri%2A>. Należy także zdefiniować `public static void Main()` metodę w klasie w projekcie. Ta klasa pojawi się w **obiekt początkowy** listy jako *ProjectName.ClassName*. Klasę można następnie wybrać jako obiekt początkowy.

Zobacz [/main (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) Aby uzyskać więcej informacji. Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.StartupObject%2A>.

**Informacje o zestawie**

Ten przycisk otwiera [informacje o zestawie](../../ide/reference/assembly-information-dialog-box.md) okno dialogowe.

## <a name="resources"></a>Resources

**Zasobów** opcje ułatwiające konfigurowanie ustawień zasobów dla aplikacji.

**Ikony i manifestu**

Domyślnie ten przycisk radiowy zostanie wybrany i **ikonę** i **manifestu** opcje są włączone. Dzięki temu można własną ikonę lub wybrać opcje różnych generowania manifestu. Pozostaw ten przycisk radiowy zaznaczone, chyba że udostępniasz plik zasobów dla projektu.

**Ikona**

Zestawy *.ico* plik, który ma być używany jako ikona programu. Kliknij przycisk **Przeglądaj** Przeglądaj w poszukiwaniu istniejącej grafiki, lub wpisz nazwę pliku, którego chcesz. Zobacz [/win32icon (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) Aby uzyskać więcej informacji.

Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.

**Manifest**

Wybiera opcję generowania manifestu, gdy aplikacja zostanie uruchomiona w systemie Windows Vista w ramach kontroli konta użytkownika (UAC). Ta opcja może mieć następujące wartości:

- **Osadź manifest z ustawieniami domyślnymi**. Obsługuje typowy sposób, w którym działa program Visual Studio na Windows Vista, czyli do osadzenia informacji o zabezpieczeniach w pliku wykonywalnym aplikacji, określając, że `requestedExecutionLevel` można `AsInvoker`. Jest to opcja domyślna.

- **Tworzenie aplikacji bez manifestu**. Ta metoda jest określana jako *wirtualizacji*. Użyj tej opcji w celu zachowania zgodności ze starszymi aplikacjami.

- **Properties\app.manifest**. Ta opcja jest wymagana w przypadku aplikacji wdrożonych przez ClickOnce lub rejestracji wolnego modelu COM. W przypadku publikowania aplikacji za pomocą wdrażania ClickOnce **manifestu** jest automatycznie ustawiona na tę opcję.

**Plik zasobów**

Wybierz ten przycisk radiowy, gdy udostępniasz plik zasobów dla projektu. Wybranie tej opcji wyłącza **ikonę** i **manifestu** opcje.

Wprowadź nazwę ścieżki lub użyj przycisku Przeglądaj (**...** ) aby dodać plik zasobów Win32 do projektu.