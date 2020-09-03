---
title: Strona aplikacji, Projektant projektu (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
ms.assetid: f13701a8-4e2e-4474-9d60-bb43decbe0c1
caps.latest.revision: 61
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2bf9c64a55f6f3b49cb1e0a50fa532f276394dac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852002"
---
# <a name="application-page-project-designer-c"></a>Strona aplikacji, Projektant projektu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użyj strony **aplikacji** **projektanta projektu** , aby określić ustawienia i właściwości aplikacji projektu.

 Aby uzyskać dostęp do strony **aplikacji** , wybierz węzeł projektu (nie węzeł **rozwiązania** ) w **Eksplorator rozwiązań**. Następnie wybierz **projekt**, **Właściwości** na pasku menu. Gdy pojawi się Projektant projektu, kliknij kartę **aplikacja** .

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="general-application-settings"></a>Ogólne ustawienia aplikacji
 Poniższe opcje umożliwiają skonfigurowanie ustawień ogólnych dla aplikacji.

 **Nazwa zestawu** Określa nazwę pliku wyjściowego, który będzie przechowywać manifest zestawu. Zmiana tej właściwości spowoduje również zmianę właściwości **Nazwa wyjściowa** . Możesz również wprowadzić tę zmianę z poziomu wiersza polecenia, używając [/out (opcje kompilatora C#)](https://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5). Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.AssemblyName%2A> .

 **Domyślna przestrzeń nazw** Określa podstawową przestrzeń nazw dla plików dodanych do projektu.

 Aby uzyskać więcej informacji na temat tworzenia przestrzeni nazw w kodzie, zobacz [przestrzeń nazw](https://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) .

 Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.RootNamespace%2A> .

 **Platforma docelowa** Określa wersję .NET Framework, do której należy aplikacja. Ta opcja może mieć różne wartości w zależności od wersji .NET Framework zainstalowanych na komputerze.

 Domyślnie wartość jest taka sama jak platforma docelowa wybrana w oknie dialogowym **Nowy projekt** .

> [!NOTE]
> Wstępnie wymagane pakiety wymienione w [oknie dialogowym wymagania wstępne](../../ide/reference/prerequisites-dialog-box.md) są ustawiane automatycznie przy pierwszym otwarciu okna dialogowego. Jeśli później zmienisz platformę docelową projektu, musisz ręcznie wybrać wymagania wstępne, aby dopasować ją do nowej platformy docelowej.

 Aby uzyskać więcej informacji, zobacz [How to: Targeting](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) a [Visual Studio — omówienie wielu](../../ide/visual-studio-multi-targeting-overview.md).NET Framework elementów docelowych.

 **Typ aplikacji** Określa typ aplikacji do skompilowania. W przypadku [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikacji można określić **aplikację ze sklepu Windows**, **bibliotekę klas**lub **plik WinMD**. W przypadku większości innych typów aplikacji można określić **aplikację systemu Windows**, **aplikację konsolową**, **bibliotekę klas**, **usługę systemu Windows**lub **bibliotekę formantów sieci Web**.

 Dla projektu aplikacji sieci Web należy określić **bibliotekę klas**.

 W przypadku określenia opcji **pliku winmd** typy mogą być rzutowane na dowolny język programowania środowisko wykonawcze systemu Windows. Przez pakowanie danych wyjściowych projektu jako pliku WinMD, można zakodować aplikację w wielu językach i współdziałać z kodem, tak jakby były one napisane w tym samym języku. Tę opcję można określić dla rozwiązań przeznaczonych dla bibliotek środowisko wykonawcze systemu Windows, w tym [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [Tworzenie składników Środowisko wykonawcze systemu Windows w językach C# i Visual Basic](https://msdn.microsoft.com/library/windows/apps/br230301(v=VS.85).aspx).

> [!NOTE]
> Środowisko wykonawcze systemu Windows można projektować typów, tak aby były one widoczne jako obiekty natywne w zależności od używanego języka. Na przykład aplikacje JavaScript, które współpracują z środowisko wykonawcze systemu Windows używają go jako zestawu obiektów JavaScript, a aplikacje C# używają biblioteki jako kolekcji obiektów .NET. Przez pakowanie danych wyjściowych projektu jako pliku WinMD można skorzystać z tej samej technologii, która środowisko wykonawcze systemu Windows używa.

 Aby uzyskać więcej informacji na temat właściwości **typu aplikacji** , zobacz [/Target (opcje kompilatora C#)](https://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f). Aby uzyskać informacje na temat programistycznego uzyskiwania dostępu do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.OutputType%2A> .

 **Informacje o zestawie** Kliknięcie tego przycisku powoduje wyświetlenie okna [dialogowego Informacje o zestawie](../../ide/reference/assembly-information-dialog-box.md).

 **Obiekt startowy** Definiuje punkt wejścia, który ma być wywoływany, gdy aplikacja jest ładowana. Zwykle jest to ustawiane jako główny formularz w aplikacji lub do `Main` procedury, która powinna być uruchamiana podczas uruchamiania aplikacji. Ponieważ biblioteki klas nie mają punktu wejścia, ich jedyną opcją dla tej właściwości jest **(nie ustawiono)**.

 Domyślnie w projekcie aplikacji przeglądarki WPF ta opcja jest **(nie ustawiana)**. Drugą opcją jest *ProjectName*. app. W tym rodzaju projekcie należy ustawić początkowy identyfikator URI, aby załadować zasób interfejsu użytkownika podczas uruchamiania aplikacji. Aby to zrobić, Otwórz plik Application. XAML w projekcie i ustaw `StartupUri` Właściwość na plik. XAML w projekcie, na przykład window1. XAML. Aby uzyskać listę dopuszczalnych elementów głównych, zobacz <xref:System.Windows.Application.StartupUri%2A> . Należy również zdefiniować `public static void Main()` metodę w klasie w projekcie. Ta klasa będzie wyświetlana na liście **obiektów uruchamiania** jako *ProjectName. ClassName*. Następnie można wybrać klasę jako obiekt startowy.

 Aby uzyskać więcej informacji, zobacz [/Main (opcje kompilatora C#)](https://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049) . Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.StartupObject%2A> .

## <a name="resources"></a>Zasoby
 Poniższe opcje umożliwiają skonfigurowanie ustawień ogólnych dla aplikacji.

 **Ikona i manifest** Domyślnie ten przycisk radiowy jest zaznaczony, a **ikona** i opcje **manifestu** są włączone. Dzięki temu można wybrać własną ikonę lub wybrać różne opcje generowania manifestu. Ten przycisk radiowy należy pozostawić, chyba że podajesz plik zasobów dla projektu.

 **Ikona** Ustawia plik ICO, który ma być używany jako ikona programu. Kliknij przycisk wielokropka, aby wyszukać istniejącą grafikę, lub wpisz nazwę pliku, który chcesz. Aby uzyskać więcej informacji, zobacz [/win32icon (opcje kompilatora C#)](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138) . Aby programowo uzyskać dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A> .

 **Manifest** Wybiera opcję generowania manifestu, gdy aplikacja jest uruchamiana w systemie Windows Vista w ramach kontroli konta użytkownika (UAC). Ta opcja może mieć następujące wartości:

- **Osadź manifest z ustawieniami domyślnymi**. Obsługuje typowy sposób, w jaki program Visual Studio działa w systemie Windows Vista, który polega na osadzeniu informacji o zabezpieczeniach w pliku wykonywalnym `requestedExecutionLevel` aplikacji `AsInvoker` . Jest to domyślne ustawienie opcji.

- **Utwórz aplikację bez manifestu**. Ta metoda jest znana jako *Wirtualizacja*. Użyj tej opcji, aby zapewnić zgodność ze starszymi aplikacjami.

- **Properties\app.manifest**. Ta opcja jest wymagana w przypadku aplikacji wdrażanych za pomocą technologii ClickOnce lub COM bez rejestracji. Jeśli opublikujesz aplikację przy użyciu wdrożenia ClickOnce, **manifest** jest automatycznie ustawiany na tę opcję.

  **Plik zasobów** Wybierz ten przycisk radiowy, gdy udostępniasz plik zasobów dla projektu. Wybranie tej opcji powoduje wyłączenie opcji **ikony** i **manifestu** .

  Wprowadź nazwę ścieżki lub użyj przycisku przeglądania (**...**), aby dodać plik zasobów Win32 do projektu.

## <a name="see-also"></a>Zobacz też
[Zarządzanie właściwościami aplikacji](../../ide/application-properties.md) [pisanie kodu w rozwiązaniach pakietu Office](https://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)
