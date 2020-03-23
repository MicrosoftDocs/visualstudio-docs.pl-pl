---
title: Strona aplikacji właściwości projektu w języku C#
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595829"
---
# <a name="application-page-project-designer-c"></a>Strona aplikacji, Projektant projektu (C#)

Użyj **aplikacji** strony **Projektanta projektu,** aby określić ustawienia i właściwości aplikacji projektu.

Aby uzyskać dostęp do strony **Aplikacji,** wybierz węzeł projektu (a nie węzeł **Rozwiązanie)** w **Eksploratorze rozwiązań**. Następnie wybierz polecenie**Właściwości** **projektu** > na pasku menu. Po wyświetleniu **projektanta projektu** kliknij kartę **Aplikacja.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>Ogólne ustawienia aplikacji

Poniższe opcje umożliwiają skonfigurowanie ustawień ogólnych dla aplikacji.

**Nazwa zestawu**

Określa nazwę pliku wyjściowego, który będzie zawierać manifest zestawu. Zmiana tej właściwości powoduje również zmianę właściwości **Nazwa wyjściowa.**

Tę zmianę można również wprowadzić w wierszu polecenia za pomocą [opcji /out (Opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/out-compiler-option)

Aby uzyskać dostęp do tej <xref:VSLangProj.ProjectProperties.AssemblyName%2A>właściwości programowo, zobacz .

**Domyślna przestrzeń nazw**

Określa podstawową przestrzeń nazw dla plików dodanych do projektu.

Zobacz [obszar nazw, aby](/dotnet/csharp/language-reference/keywords/namespace) uzyskać więcej informacji na temat tworzenia obszarów nazw w kodzie.

Aby uzyskać dostęp do tej <xref:VSLangProj.ProjectProperties.RootNamespace%2A>właściwości programowo, zobacz .

**Struktura docelowa**

Określa wersję platformy .NET przeznaczoną dla aplikacji. Ta opcja może mieć różne wartości w zależności od tego, które wersje platformy .NET są zainstalowane na komputerze.

W przypadku projektów programu .NET Framework wartość domyślna jest zgodna z platformą docelową określoną podczas tworzenia projektu.

W przypadku projektu przeznaczonego dla programu .NET Core dostępne wersje mogą być wyświetlane w następujący sposób:

![Docelowe wersje struktury dla projektu .NET Core](../media/application-target-framework.png)

> [!NOTE]
> Pakiety wymagań wstępnych wymienione w [oknie dialogowym Wymagania wstępne](../../ide/reference/prerequisites-dialog-box.md) są ustawiane automatycznie przy pierwszym otwarciu okna dialogowego. Jeśli następnie zmienisz platformę docelową projektu, należy ręcznie wybrać wymagania wstępne, aby dopasować się do nowej struktury docelowej.

Aby uzyskać więcej informacji, zobacz [omówienie kierowania na ramy](../../ide/visual-studio-multi-targeting-overview.md).

**Typ wyjścia**

Określa typ aplikacji do utworzenia. Wartości różnią się w zależności od typu projektu. Na przykład dla projektu **aplikacji konsoli** można określić aplikację **systemu Windows,** **aplikację konsoli**lub **bibliotekę klas** jako typ wyjściowy.

W przypadku projektu aplikacji sieci web należy określić **bibliotekę klas**.

Aby uzyskać więcej informacji na temat właściwości **Typ wyjścia,** zobacz [/target (Opcje kompilatora C#).](/dotnet/csharp/language-reference/compiler-options/target-compiler-option)

Aby uzyskać informacje dotyczące programowego dostępu <xref:VSLangProj.ProjectProperties.OutputType%2A>do tej właściwości, zobacz .

**Automatyczne generowanie przekierowań wiązania**

Przekierowania powiązania są dodawane do projektu, jeśli aplikacja lub jej składniki odwołują się do więcej niż jednej wersji tego samego zestawu. Jeśli chcesz ręcznie zdefiniować przekierowania powiązania w pliku projektu, usuń zaznaczenie **przekierowywania powiązania autogeneruj**.

Aby uzyskać więcej informacji na temat przekierowania, zobacz [Przekierowywanie wersji zestawu](/dotnet/framework/configure-apps/redirect-assembly-versions).

**Obiekt startowy**

Definiuje punkt wejścia, który ma być wywoływany podczas ładowania aplikacji. Ogólnie jest to ustawione albo do formularza głównego w `Main` aplikacji lub do procedury, która powinna być uruchamiana po uruchomieniu aplikacji. Ponieważ biblioteki klas nie mają punktu wejścia, ich jedyną opcją dla tej właściwości jest **(Nie ustawiono).**

Domyślnie w projekcie aplikacji WPF ta opcja jest ustawiona na **(Nie ustawiono)**. Inną opcją \[jest projectname].App. W projekcie WPF należy ustawić identyfikator URI uruchamiania, aby załadować zasób interfejsu użytkownika po uruchomieniu aplikacji. Aby to zrobić, otwórz plik *Application.xaml* w `StartupUri` projekcie i ustaw właściwość na plik *xaml* w projekcie, na przykład *Window1.xaml*. Aby uzyskać listę dopuszczalnych <xref:System.Windows.Application.StartupUri%2A>elementów głównych, zobacz . Należy również zdefiniować `public static void Main()` metodę w klasie w projekcie. Ta klasa pojawi się na liście **obiektów uruchamiania** jako *ProjectName.ClassName*. Następnie można wybrać klasę jako obiekt startowy.

Aby uzyskać więcej informacji, zobacz [/main (Opcje kompilatora Języka C#).](/dotnet/csharp/language-reference/compiler-options/main-compiler-option) Aby uzyskać dostęp do tej <xref:VSLangProj.ProjectProperties.StartupObject%2A>właściwości programowo, zobacz .

**Informacje o montażu**

Ten przycisk powoduje otwarcie okna dialogowego [Informacje o złożeniu.](../../ide/reference/assembly-information-dialog-box.md)

## <a name="resources"></a>Zasoby

Opcje **Zasoby** ułatwiają konfigurowanie ustawień zasobów dla aplikacji.

**Ikona i manifest**

Domyślnie ten przycisk opcji jest zaznaczony, a opcje **Ikona** i **Manifest** są włączone. Dzięki temu można wybrać własną ikonę lub wybrać różne opcje generowania manifestu. Pozostaw ten przycisk opcji wybrany, chyba że udostępniasz plik zasobów dla projektu.

**Ikona**:

Ustawia plik *.ico,* którego chcesz użyć jako ikony programu. Kliknij **przycisk Przeglądaj,** aby wyszukać istniejącą grafikę, lub wpisz odpowiednią nazwę pliku. Zobacz [/win32icon (Opcje kompilatora C#),](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option) aby uzyskać więcej informacji.

Aby uzyskać dostęp do tej <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>właściwości programowo, zobacz .

Aby uzyskać informacje na temat tworzenia ikony, zobacz [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons).

**Manifest**

Wybiera opcję generowania manifestu, gdy aplikacja działa w systemie Windows Vista w obszarze Kontrola konta użytkownika (Kontrola konta użytkownika). Ta opcja może mieć następujące wartości:

- **Osadź manifest z ustawieniami domyślnymi**. Obsługuje typowy sposób, w jaki program Visual Studio działa w systemie Windows Vista, który polega na `requestedExecutionLevel` osadzanie informacji o zabezpieczeniach w pliku wykonywalnym aplikacji, określając, że jest `AsInvoker`. Jest to domyślne ustawienie opcji.

- **Tworzenie aplikacji bez manifestu**. Ta metoda jest znana jako *wirtualizacja*. Użyj tej opcji, aby uzyskać zgodność z wcześniejszymi aplikacjami.

- **Właściwości\app.manifest**. Ta opcja jest wymagana dla aplikacji wdrożonych przez ClickOnce lub Registration-Free COM. Jeśli publikujesz aplikację przy użyciu clickonce **wdrożenia, Manifest** jest automatycznie ustawiana na tę opcję.

**Plik zasobów**

Wybierz ten przycisk opcji podczas podawania pliku zasobów dla projektu. Wybranie tej opcji powoduje wyłączenie opcji **Ikona** i **Manifest.**

Wprowadź nazwę ścieżki lub użyj przycisku Przeglądaj (**...**), aby dodać plik zasobu Win32 do projektu.

Aby uzyskać więcej informacji, zobacz [Tworzenie plików zasobów dla aplikacji .NET](/dotnet/framework/resources/creating-resource-files-for-desktop-apps).
