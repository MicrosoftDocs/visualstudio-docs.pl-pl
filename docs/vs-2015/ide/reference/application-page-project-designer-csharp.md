---
title: Strona aplikacji, Projektant projektu (C#) | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1c1c463e95ab81c0331b12aaea692afe7005eff9
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59653701"
---
# <a name="application-page-project-designer-c"></a>Strona aplikacji, Projektant projektu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użyj **aplikacji** strony **projektanta projektu** do określania ustawień aplikacji i właściwości projektu.  
  
 Aby uzyskać dostęp do **aplikacji** wybierz węzeł projektu (nie **rozwiązania** węźle) w **Eksploratora rozwiązań**. Następnie wybierz **projektu**, **właściwości** na pasku menu. Gdy pojawi się w Projektancie projektu, kliknij przycisk **aplikacji** kartę.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="general-application-settings"></a>Ustawienia ogólne aplikacji  
 Poniższe opcje umożliwiają konfigurowanie ogólnych ustawień dla aplikacji.  
  
 **Nazwa zestawu**  
 Określa nazwę pliku wyjściowego, który będzie przechowywać manifest zestawu. Zmiana tej właściwości spowoduje również zmianę **Nazwa wyjściowego** właściwości. Można również wprowadzenie tej zmiany z wiersza polecenia przy użyciu [/out (opcje kompilatora C#)](http://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5). Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.  
  
 **Domyślna przestrzeń nazw**  
 Określa podstawowej przestrzeni nazw dla plików dodawane do projektu.  
  
 Zobacz [przestrzeni nazw](http://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) Aby uzyskać więcej informacji na temat tworzenia przestrzeni nazw w kodzie.  
  
 Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.  
  
 **Struktura docelowa**  
 Określa wersję programu .NET Framework, cele aplikacji. Ta opcja może mieć różne wartości w zależności od tego, które wersje programu .NET Framework są zainstalowane na tym komputerze.  
  
 Domyślnie wartość jest taka sama jak platforma docelowa, które wybrano w **nowy projekt** okno dialogowe.  
  
> [!NOTE]
>  Wstępnie wymagane pakiety wymienione w [wstępnie wymagane składniki, okno dialogowe](../../ide/reference/prerequisites-dialog-box.md) są ustawiane automatycznie przy pierwszym otwarciu okna dialogowego. Jeśli użytkownik zmieni później platformę docelową projektu, trzeba będzie wybrać wstępnie wymagane składniki ręcznie, aby dopasować do nowej platformy docelowej.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](../../ide/how-to-target-a-version-of-the-dotnet-framework.md) i [programu Visual Studio Wielowersyjnością kodu – Przegląd](../../ide/visual-studio-multi-targeting-overview.md).  
  
 **Typ aplikacji**  
 Określa typ aplikacji pozwalają na tworzenie. Aby uzyskać [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikacji, można określić **Windows Store App**, **biblioteki klas**, lub **plik WinMD**. W przypadku większości innych typów aplikacji, możesz określić **aplikacji Windows**, **aplikację Konsolową**, **biblioteki klas**, **usługi Windows**, lub **Biblioteka formantów sieci Web**.  
  
 W przypadku projektu aplikacji sieci web, należy określić **biblioteki klas**.  
  
 Jeśli określisz **plik WinMD** opcji typów może zostać przedstawione dowolnego środowiska wykonawczego Windows, język programowania. Przez funkcję tworzenia pakietów danych wyjściowych projektu jako plik WinMD, kod aplikacji w wielu językach i współdziałania tak, jakby jego autorem kod w języku. Można określić tę opcję, aby rozwiązania przeznaczone dla bibliotek środowiska wykonawczego Windows, w tym [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [Tworzenie składników środowiska wykonawczego Windows w języku C# i Visual Basic](http://go.microsoft.com/fwlink/?LinkId=231895).  
  
> [!NOTE]
>  Środowisko wykonawcze Windows można typów projektów, aby były wyświetlane jako obiektów natywnych w jakikolwiek język są one używane. Na przykład JavaScript aplikacji współdziałających ze środowiska wykonawczego Windows ich używać jako zbiór obiektów JavaScript i aplikacji w języku C# korzystanie z biblioteki jako kolekcję obiektów platformy .NET. Upakowanie danych wyjściowych projektu w formacie pliku WinMD, możesz korzystać z zalet tej samej technologii, która używa środowiska wykonawczego Windows.  
  
 Aby uzyskać więcej informacji na temat **typ aplikacji** właściwości, zobacz [/TARGET (opcje kompilatora C#)](http://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f). Aby dowiedzieć się, jak programowo dostęp do tej właściwości, zobacz <xref:VSLangProj.ProjectProperties.OutputType%2A>.  
  
 **Informacje o zestawie**  
 Kliknięcie tego przycisku powoduje wyświetlenie [informacje o zestawie — okno dialogowe](../../ide/reference/assembly-information-dialog-box.md).  
  
 **Obiekt początkowy**  
 Definiuje punkt wejścia, który ma być wywoływana podczas ładowania aplikacji. Zazwyczaj jest ono ustawione w formularzu głównym w aplikacji lub do `Main` procedury, które należy uruchamiać podczas uruchamiania aplikacji. Ponieważ biblioteki klas nie ma punktu wejścia, ich jedyną opcją dla tej właściwości jest **(nie ustawiono)**.  
  
 Domyślnie w projekcie aplikacja przeglądarki środowiska WPF, ta opcja jest **(nie ustawiono)**. Druga opcja to *Projectname*. aplikacji. W tego rodzaju projektu należy ustawić początkową identyfikatora URI można załadować zasobów interfejsu użytkownika podczas uruchamiania aplikacji. Aby to zrobić, otwórz plik Application.xaml w projekcie i ustaw `StartupUri` właściwość w pliku .xaml w projekcie, takie jak Window1.xaml. Aby uzyskać listę elementów głównych dopuszczalne, zobacz <xref:System.Windows.Application.StartupUri%2A>. Należy także zdefiniować `public static void Main()` metodę w klasie w projekcie. Ta klasa pojawi się w **obiekt początkowy** listy jako *ProjectName.ClassName*. Klasę można następnie wybrać jako obiekt początkowy.  
  
 Zobacz [/main (opcje kompilatora C#)](http://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049) Aby uzyskać więcej informacji. Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.StartupObject%2A>.  
  
## <a name="resources"></a>Zasoby  
 Poniższe opcje umożliwiają konfigurowanie ogólnych ustawień dla aplikacji.  
  
 **Ikony i manifestu**  
 Domyślnie ten przycisk radiowy zostanie wybrany i **ikonę** i **manifestu** opcje są włączone. Dzięki temu można własną ikonę lub wybrać opcje różnych generowania manifestu. Pozostaw ten przycisk radiowy zaznaczone, chyba że udostępniasz plik zasobów dla projektu.  
  
 **Ikona**  
 Określa plik .ico, który ma być używany jako ikona programu. Kliknij przycisk wielokropka, aby przejść do istniejącej grafiki, lub wpisz nazwę pliku, którego chcesz. Zobacz [/win32icon (opcje kompilatora C#)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138) Aby uzyskać więcej informacji. Aby uzyskać dostęp do tej właściwości programowo, zobacz <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>.  
  
 **Manifest**  
 Wybiera opcję generowania manifestu, gdy aplikacja zostanie uruchomiona w systemie Windows Vista w ramach kontroli konta użytkownika (UAC). Ta opcja może mieć następujące wartości:  
  
- **Osadź manifest z ustawieniami domyślnymi**. Obsługuje typowy sposób, w którym działa program Visual Studio na Windows Vista, czyli do osadzenia informacji o zabezpieczeniach w pliku wykonywalnym aplikacji, określając, że `requestedExecutionLevel` można `AsInvoker`. Jest to opcja domyślna.  
  
- **Tworzenie aplikacji bez manifestu**. Ta metoda jest określana jako *wirtualizacji*. Użyj tej opcji w celu zachowania zgodności ze starszymi aplikacjami.  
  
- **Properties\app.manifest**. Ta opcja jest wymagana w przypadku aplikacji wdrożonych przez ClickOnce lub rejestracji wolnego modelu COM. W przypadku publikowania aplikacji za pomocą wdrażania ClickOnce **manifestu** jest automatycznie ustawiona na tę opcję.  
  
  **Plik zasobów**  
  Wybierz ten przycisk radiowy, udostępniając plik zasobów dla projektu. Wybranie tej opcji wyłącza **ikonę** i **manifestu** opcje.  
  
  Wprowadź nazwę ścieżki lub użyj przycisku Przeglądaj (**...** ) aby dodać plik zasobów Win32 do projektu.  
  
## <a name="see-also"></a>Zobacz też  
[Zarządzanie właściwościami aplikacji](../../ide/application-properties.md)  
 [Pisanie kodu dla rozwiązań pakietu Office](http://msdn.microsoft.com/library/2d4d8fd0-e881-4829-976f-0d1a9221dec0)
