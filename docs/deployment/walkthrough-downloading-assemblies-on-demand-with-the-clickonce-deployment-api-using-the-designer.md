---
title: 'Wskazówki: Pobieranie zestawów na żądanie przy użyciu interfejsu API przy użyciu narzędzia Projektant wdrażania ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 20df3172b2745a50f697b09ffe0bf95eaad4f39f
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389004"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>Wskazówki: Pobieranie zestawów na żądanie z wdrożeniem ClickOnce interfejsu API przy użyciu narzędzia Projektant
Domyślnie wszystkie zestawy zawarte w [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji zostaną pobrane po pierwszym uruchomieniu aplikacji. Jednak może być częścią aplikacji, które są używane w małej grupie użytkowników. W tym przypadku chcesz pobrać zestaw tylko wtedy, gdy tworzysz w jednym z jej typów. Następujące Instruktaż pokazuje, jak oznaczyć określone zestawy w aplikacji jako "opcjonalny", jak je pobrać za pomocą klasy i w <xref:System.Deployment.Application> przestrzenią nazw, gdy wymagane przez środowisko uruchomieniowe języka wspólnego.

> [!NOTE]
> Aplikacja będzie mieć do uruchamiania w trybie pełnego zaufania, aby użyć tej procedury.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

## <a name="create-the-projects"></a>Tworzenie projektów

### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Aby utworzyć projekt, który używa zestawu na żądanie przy użyciu programu Visual Studio

1. Utwórz nowy projekt Windows Forms w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Na **pliku** menu wskaż **Dodaj**, a następnie kliknij przycisk **nowy projekt**. Wybierz **biblioteki klas** projektu w oknie dialogowym, a następnie nadaj mu nazwę `ClickOnceLibrary`.

   > [!NOTE]
   >  W języku Visual Basic, zaleca się zmodyfikowanie właściwości projektu, aby zmienić przestrzeń nazw korzenia dla tego projektu do `Microsoft.Samples.ClickOnceOnDemand` lub do wybranej przestrzeni nazw. Dla uproszczenia dwa projekty w tym przewodniku znajdują się w tej samej przestrzeni nazw.

2. Zdefiniuj klasę o nazwie `DynamicClass` za pomocą pojedynczej właściwości o nazwie `Message`.

    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]

3. Wybierz projekt Windows Forms w **Eksploratora rozwiązań**. Dodaj odwołanie do <xref:System.Deployment.Application> zestawu i projekt odwołuje się do `ClickOnceLibrary` projektu.

   > [!NOTE]
   >  W języku Visual Basic, zaleca się zmodyfikowanie właściwości projektu, aby zmienić przestrzeń nazw korzenia dla tego projektu do `Microsoft.Samples.ClickOnceOnDemand` lub do wybranej przestrzeni nazw. Dla uproszczenia dwa projekty w tym przewodniku znajdują się w tej samej przestrzeni nazw.

4. Kliknij prawym przyciskiem myszy formularz, kliknij przycisk **Wyświetl kod** z menu i dodaj następujące odwołania do formularza.

    [!code-csharp[ClickOnceOnDemand#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.cs)]
    [!code-vb[ClickOnceOnDemand#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]

5. Dodaj następujący kod do pobierania tego zestawu na żądanie. Ten kod pokazuje jak mapować zbiór zestawów, do nazwy grupy, za pomocą rodzajowego <xref:System.Collections.DictionaryBase.Dictionary%2A> klasy. Ponieważ pobierane są tylko jednego zestawu, w tym przewodniku, istnieje tylko jeden zestaw w naszej grupy. W rzeczywistej aplikacji prawdopodobnie chcesz pobrać wszystkie zestawy związane z pojedynczej funkcji w aplikacji w taki sposób, w tym samym czasie. W tabeli mapowania można łatwo to zrobić przez skojarzenie wszystkich bibliotek DLL, które należą do funkcji z nazwą grupy pobierania.

    [!code-csharp[ClickOnceOnDemand#2](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.cs)]
    [!code-vb[ClickOnceOnDemand#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]

6. Na **widoku** menu, kliknij przycisk **przybornika**. Przeciągnij <xref:System.Windows.Forms.Button> z **przybornika** na formularz. Kliknij dwukrotnie przycisk, a następnie dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń.

    [!code-csharp[ClickOnceOnDemand#3](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_4.cs)]
    [!code-vb[ClickOnceOnDemand#3](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_4.vb)]

## <a name="mark-assemblies-as-optional"></a>Oznacz zestawy jako opcjonalne

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Aby oznaczyć zestawów jako opcjonalne w aplikacji ClickOnce za pomocą programu Visual Studio

1.  Kliknij prawym przyciskiem myszy projekt Windows Forms w **Eksploratora rozwiązań** i kliknij przycisk **właściwości**. Wybierz **Publikuj** kartę.

2.  Kliknij przycisk **pliki aplikacji** przycisku.

3.  Znajdź listę dla *ClickOnceLibrary.dll*. Ustaw **stan publikowania** pole listy rozwijanej, aby **Include**.

4.  Rozwiń **grupy** pole listy rozwijanej i wybierz pozycję **New**. Wprowadź nazwę `ClickOnceLibrary` jako nazwę nowej grupy.

5.  Kontynuować publikowanie aplikacji, zgodnie z opisem w [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Aby oznaczyć zestawów jako opcjonalne w aplikacji ClickOnce przy użyciu Manifest Generation i narzędzia do edytowania — graficzny klient (MageUI.exe)

1. Utwórz swoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty zgodnie z opisem w [wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2. Przed jego zamknięciem, MageUI.exe, wybierz kartę która zawiera manifest aplikacji danego wdrożenia, a następnie na karcie Wybierz **pliki** kartę.

3. Znajdź ClickOnceLibrary.dll na liście plików aplikacji i ustaw jego **typ pliku** kolumny **Brak**. Aby uzyskać **grupy** wpisz `ClickOnceLibrary.dll`.

## <a name="test-the-new-assembly"></a>Nowy zestaw testów

Aby przetestować zestaw na żądanie:

1. Rozpocznij aplikacja wdrożona za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].

2. Gdy pojawi się główny formularz, naciśnij klawisz <xref:System.Windows.Forms.Button>. Powinien zostać wyświetlony ciąg w okno komunikatu, która odczytuje "Hello, World!"

## <a name="see-also"></a>Zobacz także

- <xref:System.Deployment.Application.ApplicationDeployment>