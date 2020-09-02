---
title: Strona aplikacji właściwości projektu C#
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ef9a38fc13d0d9c9f6b912f4cb2b83971d105c29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595829"
---
# <a name="application-page-project-designer-c"></a>Strona aplikacji, Projektant projektu (C#)

Użyj strony **aplikacji** **projektanta projektu** , aby określić ustawienia i właściwości aplikacji projektu.

Aby uzyskać dostęp do strony **aplikacji** , wybierz węzeł projektu (nie węzeł **rozwiązania** ) w **Eksplorator rozwiązań**. Następnie wybierz **Project**  >  **Właściwości** projektu na pasku menu. Gdy pojawi się **Projektant projektu** , kliknij kartę **aplikacja** .

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Ogólne ustawienia aplikacji

Poniższe opcje umożliwiają skonfigurowanie ustawień ogólnych dla aplikacji.

**Nazwa zestawu**

Określa nazwę pliku wyjściowego, który będzie przechowywać manifest zestawu. Zmiana tej właściwości powoduje także zmianę właściwości **nazwy wyjściowej** .

Możesz również wprowadzić tę zmianę z poziomu wiersza polecenia, używając [/out (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).

Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.AssemblyName%2A> .

**Domyślna przestrzeń nazw**

Określa podstawową przestrzeń nazw dla plików dodanych do projektu.

Aby uzyskać więcej informacji na temat tworzenia przestrzeni nazw w kodzie, zobacz [przestrzeń nazw](/dotnet/csharp/language-reference/keywords/namespace) .

Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.RootNamespace%2A> .

**Struktura docelowa**

Określa wersję programu .NET, która jest przeznaczona dla aplikacji. Ta opcja może mieć różne wartości w zależności od tego, które wersje platformy .NET są zainstalowane na komputerze.

W przypadku projektów .NET Framework wartość domyślna jest zgodna z platformą docelową, która została określona podczas tworzenia projektu.

Dla projektu, który jest przeznaczony dla platformy .NET Core, dostępne wersje mogą wyglądać następująco:

![Wersje platformy docelowej dla projektu .NET Core](../media/application-target-framework.png)

> [!NOTE]
> Wstępnie wymagane pakiety wymienione w [oknie dialogowym wymagania wstępne](../../ide/reference/prerequisites-dialog-box.md) są ustawiane automatycznie przy pierwszym otwarciu okna dialogowego. Jeśli później zmienisz platformę docelową projektu, musisz ręcznie wybrać wymagania wstępne, aby dopasować ją do nowej platformy docelowej.

Aby uzyskać więcej informacji, zobacz temat [Omówienie funkcji określania wartości docelowej](../../ide/visual-studio-multi-targeting-overview.md).

**Typ danych wyjściowych**

Określa typ aplikacji do skompilowania. Wartości są różne w zależności od typu projektu. Na przykład dla projektu **aplikacji konsoli** można określić **aplikację systemu Windows**, **aplikację konsolową**lub **bibliotekę klas** jako typ danych wyjściowych.

Dla projektu aplikacji sieci Web należy określić **bibliotekę klas**.

Aby uzyskać więcej informacji na temat właściwości **Typ danych wyjściowych** , zobacz [/Target (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).

Aby uzyskać informacje na temat programistycznego uzyskiwania dostępu do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.OutputType%2A> .

**Automatyczne generowanie przekierowań powiązań**

Przekierowania powiązań są dodawane do projektu, jeśli aplikacja lub jej składniki odwołują się do więcej niż jednej wersji tego samego zestawu. Jeśli chcesz ręcznie zdefiniować przekierowania powiązań w pliku projektu, usuń zaznaczenie opcji **automatycznie Generuj przekierowania powiązań**.

Aby uzyskać więcej informacji na temat przekierowania, zobacz Przekierowywanie [wersji zestawu](/dotnet/framework/configure-apps/redirect-assembly-versions).

**Obiekt startowy**

Definiuje punkt wejścia, który ma być wywoływany, gdy aplikacja jest ładowana. Zwykle jest to ustawiane jako główny formularz w aplikacji lub do `Main` procedury, która powinna być uruchamiana podczas uruchamiania aplikacji. Ponieważ biblioteki klas nie mają punktu wejścia, ich jedyną opcją dla tej właściwości jest **(nie ustawiono)**.

Domyślnie w projekcie aplikacji WPF ta opcja jest ustawiona na **(nie ustawiono)**. Druga opcja to \[ ProjectName]. app. W projekcie WPF należy ustawić początkowy identyfikator URI, aby załadować zasób interfejsu użytkownika podczas uruchamiania aplikacji. Aby to zrobić, Otwórz plik *Application. XAML* w projekcie i ustaw `StartupUri` Właściwość na plik *. XAML* w projekcie, na przykład *window1. XAML*. Aby uzyskać listę dopuszczalnych elementów głównych, zobacz <xref:System.Windows.Application.StartupUri%2A> . Należy również zdefiniować `public static void Main()` metodę w klasie w projekcie. Ta klasa będzie wyświetlana na liście **obiektów uruchamiania** jako *ProjectName. ClassName*. Następnie można wybrać klasę jako obiekt startowy.

Aby uzyskać więcej informacji, zobacz [/Main (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) . Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.StartupObject%2A> .

**Informacje o zestawie**

Ten przycisk otwiera okno dialogowe [Informacje o zestawie](../../ide/reference/assembly-information-dialog-box.md) .

## <a name="resources"></a>Zasoby

Opcje **zasobów** ułatwiają konfigurowanie ustawień zasobów aplikacji.

**Ikona i manifest**

Domyślnie ten przycisk radiowy jest zaznaczony, a **ikona** i opcje **manifestu** są włączone. Dzięki temu można wybrać własną ikonę lub wybrać różne opcje generowania manifestu. Pozostaw wybrany przycisk radiowy, chyba że udostępniasz plik zasobów dla projektu.

**Ikona**

Ustawia plik *ICO* , który ma być używany jako ikona programu. Kliknij przycisk **Przeglądaj** , aby przejść do istniejącej grafiki lub wpisz nazwę żądanego pliku. Aby uzyskać więcej informacji, zobacz [/win32icon (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) .

Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A> .

Aby uzyskać informacje na temat tworzenia ikony, zobacz [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons).

**Manifestu**

Wybiera opcję generowania manifestu, gdy aplikacja jest uruchamiana w systemie Windows Vista w ramach kontroli konta użytkownika (UAC). Ta opcja może mieć następujące wartości:

- **Osadź manifest z ustawieniami domyślnymi**. Obsługuje typowy sposób, w jaki program Visual Studio działa w systemie Windows Vista, który polega na osadzeniu informacji o zabezpieczeniach w pliku wykonywalnym `requestedExecutionLevel` aplikacji `AsInvoker` . Jest to domyślne ustawienie opcji.

- **Utwórz aplikację bez manifestu**. Ta metoda jest znana jako *Wirtualizacja*. Użyj tej opcji, aby zapewnić zgodność ze starszymi aplikacjami.

- **Properties\app.manifest**. Ta opcja jest wymagana w przypadku aplikacji wdrażanych za pomocą technologii ClickOnce lub COM bez rejestracji. Jeśli opublikujesz aplikację przy użyciu wdrożenia ClickOnce, **manifest** jest automatycznie ustawiany na tę opcję.

**Plik zasobów**

Wybierz ten przycisk radiowy, gdy udostępniasz plik zasobów dla projektu. Wybranie tej opcji powoduje wyłączenie opcji **ikony** i **manifestu** .

Wprowadź nazwę ścieżki lub użyj przycisku przeglądania (**...**), aby dodać plik zasobów Win32 do projektu.

Aby uzyskać więcej informacji, zobacz [Tworzenie plików zasobów dla aplikacji .NET](/dotnet/framework/resources/creating-resource-files-for-desktop-apps).
