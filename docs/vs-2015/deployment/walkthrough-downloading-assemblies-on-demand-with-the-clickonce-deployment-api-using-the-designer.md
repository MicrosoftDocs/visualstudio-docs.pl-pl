---
title: 'Przewodnik: Pobieranie zestawów na żądanie z wdrożeniem ClickOnce interfejsu API przy użyciu narzędzia Projektant | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4513a1fa35ab45cf36a8c86572eecd6043ee7415
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60086848"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Przewodnik: Pobieranie zestawów na żądanie z wdrożeniem ClickOnce interfejsu API przy użyciu narzędzia Projektant
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie wszystkie zestawy zawarte w [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji zostaną pobrane po pierwszym uruchomieniu aplikacji. Jednak może być częścią aplikacji, które są używane w małej grupie użytkowników. W tym przypadku chcesz pobrać zestaw tylko wtedy, gdy tworzysz w jednym z jej typów. Następujące Instruktaż pokazuje, jak oznaczyć określone zestawy w aplikacji jako "opcjonalny", jak je pobrać za pomocą klasy i w <xref:System.Deployment.Application> przestrzenią nazw, gdy wymagane przez środowisko uruchomieniowe języka wspólnego.  
  
> [!NOTE]
>  Aplikacja będzie mieć do uruchamiania w trybie pełnego zaufania, aby użyć tej procedury.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-projects"></a>Tworzenie projektów  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Aby utworzyć projekt, który używa zestawu na żądanie przy użyciu programu Visual Studio  
  
1. Utwórz nowy projekt Windows Forms w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Na **pliku** menu wskaż **Dodaj**, a następnie kliknij przycisk **nowy projekt**. Wybierz **biblioteki klas** projektu w oknie dialogowym, a następnie nadaj mu nazwę `ClickOnceLibrary`.  
  
    > [!NOTE]
    >  W języku Visual Basic, zaleca się zmodyfikowanie właściwości projektu, aby zmienić przestrzeń nazw korzenia dla tego projektu do `Microsoft.Samples.ClickOnceOnDemand` lub do wybranej przestrzeni nazw. Dla uproszczenia dwa projekty w tym przewodniku znajdują się w tej samej przestrzeni nazw.  
  
2. Zdefiniuj klasę o nazwie `DynamicClass` za pomocą pojedynczej właściwości o nazwie `Message`.  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
3. Wybierz projekt Windows Forms w **Eksploratora rozwiązań**. Dodaj odwołanie do <xref:System.Deployment.Application> zestawu i projekt odwołuje się do `ClickOnceLibrary` projektu.  
  
    > [!NOTE]
    >  W języku Visual Basic, zaleca się zmodyfikowanie właściwości projektu, aby zmienić przestrzeń nazw korzenia dla tego projektu do `Microsoft.Samples.ClickOnceOnDemand` lub do wybranej przestrzeni nazw. Dla uproszczenia dwa projekty w tym przewodniku znajdują się w tej samej przestrzeni nazw.  
  
4. Kliknij prawym przyciskiem myszy formularz, kliknij przycisk **Wyświetl kod** z menu i dodaj następujące odwołania do formularza.  
  
     [!code-csharp[ClickOnceOnDemand#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemand#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#1)]  
  
5. Dodaj następujący kod do pobierania tego zestawu na żądanie. Ten kod pokazuje jak mapować zbiór zestawów, do nazwy grupy, za pomocą rodzajowego <xref:System.Collections.DictionaryBase.Dictionary%2A> klasy. Ponieważ pobierane są tylko jednego zestawu, w tym przewodniku, istnieje tylko jeden zestaw w naszej grupy. W rzeczywistej aplikacji prawdopodobnie chcesz pobrać wszystkie zestawy związane z pojedynczej funkcji w aplikacji w taki sposób, w tym samym czasie. W tabeli mapowania można łatwo to zrobić przez skojarzenie wszystkich bibliotek DLL, które należą do funkcji z nazwą grupy pobierania.  
  
     [!code-csharp[ClickOnceOnDemand#2](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#2)]
     [!code-vb[ClickOnceOnDemand#2](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#2)]  
  
6. Na **widoku** menu, kliknij przycisk **przybornika**. Przeciągnij <xref:System.Windows.Forms.Button> z **przybornika** na formularz. Kliknij dwukrotnie przycisk, a następnie dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń.  
  
     [!code-csharp[ClickOnceOnDemand#3](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#3)]
     [!code-vb[ClickOnceOnDemand#3](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#3)]  
  
## <a name="marking-assemblies-as-optional"></a>Oznaczanie zestawów jako opcjonalne  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Aby oznaczyć zestawów jako opcjonalne w aplikacji ClickOnce za pomocą programu Visual Studio  
  
1. Kliknij prawym przyciskiem myszy projekt Windows Forms w **Eksploratora rozwiązań** i kliknij przycisk **właściwości**. Wybierz **Publikuj** kartę.  
  
2. Kliknij przycisk **pliki aplikacji** przycisku.  
  
3. Znajdź listę dla ClickOnceLibrary.dll. Ustaw **stan publikowania** pole listy rozwijanej, aby **Include**.  
  
4. Rozwiń **grupy** pole listy rozwijanej i wybierz pozycję **New**. Wprowadź nazwę `ClickOnceLibrary` jako nazwę nowej grupy.  
  
5. Kontynuować publikowanie aplikacji, zgodnie z opisem w [jak: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Aby oznaczyć zestawów jako opcjonalne w aplikacji ClickOnce przy użyciu Manifest Generation i narzędzia do edytowania — graficzny klient (MageUI.exe)  
  
1. Utwórz swoje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifesty zgodnie z opisem w [instruktażu: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2. Przed jego zamknięciem, MageUI.exe, wybierz kartę która zawiera manifest aplikacji danego wdrożenia, a następnie na karcie Wybierz **pliki** kartę.  
  
3. Znajdź ClickOnceLibrary.dll na liście plików aplikacji i ustaw jego **typ pliku** kolumny **Brak**. Aby uzyskać **grupy** wpisz `ClickOnceLibrary.dll`.  
  
## <a name="testing-the-new-assembly"></a>Testowanie nowego zestawu  
  
#### <a name="to-test-your-on-demand-assembly"></a>Aby przetestować zestaw na żądanie  
  
1. Rozpocznij aplikacja wdrożona za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
2. Gdy pojawi się główny formularz, naciśnij klawisz <xref:System.Windows.Forms.Button>. Powinien zostać wyświetlony ciąg w okno komunikatu, która odczytuje "Hello, World!"  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Deployment.Application.ApplicationDeployment>
