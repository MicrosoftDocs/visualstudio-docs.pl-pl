---
title: 'Przewodnik: Tworzenie prostą usługę WCF w formularzach Windows Forms | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 46250ad394a2fde1e7cde6f30fab9dc6d7fb579c
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615645"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Przewodnik: Tworzenie prostą usługę WCF w formularzach Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu przedstawiono sposób tworzenia prostej [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] usługi, testowania i do niego dostęp z aplikacji Windows Forms.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="creating-the-service"></a>Tworzenie usługi

#### <a name="to-create-a-wcf-service"></a>Tworzenie usługi WCF

1. Na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.

2. W **nowy projekt** okna dialogowego rozwiń **języka Visual Basic** lub **Visual C#** węzła i kliknij przycisk **WCF**, a następnie **WCF Biblioteka usługi**. Kliknij przycisk **OK** otworzyć projektu.

     ![Projekt biblioteki usługi WCF](../data-tools/media/wcf1.PNG "wcf1")

    > [!NOTE]
    > Spowoduje to utworzenie usługi pracy, przetestowane i używanych. Następujące dwa kroki pokazują, jak może zmodyfikować domyślną metodę, aby użyć innego typu danych. W rzeczywistej aplikacji należy również dodać własne funkcje do usługi.

3. ![Plik IService1](../data-tools/media/wcf2.png "wcf2")

     W **Eksploratora rozwiązań**, kliknij dwukrotnie IService1.vb lub IService1.cs i znajdź następujący wiersz:

     [!code-csharp[WCFWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1_2.cs#4)]
     [!code-vb[WCFWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1_2.vb#4)]

     Zmień typ `value` parametr `String`:

     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

     W powyższym kodzie, należy pamiętać, `<OperationContract()>` lub `[OperationContract]` atrybutów. Te atrybuty są wymagane do dowolnej metody udostępnianych przez usługę.

4. ![Plik Service1](../data-tools/media/wcf3.png "wcf3")

     W **Eksploratora rozwiązań**, kliknij dwukrotnie Service1.vb lub Service1.cs i znajdź następujący wiersz:

     [!code-csharp[WCFWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1_2.cs#5)]
     [!code-vb[WCFWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1_2.vb#5)]

     Zmień typ dla parametru wartość, aby `String`:

     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]

## <a name="testing-the-service"></a>Testowanie usługi

#### <a name="to-test-a-wcf-service"></a>Aby przetestować usługę WCF

1. Naciśnij klawisz **F5** do uruchamiania usługi. A **klienta testowego WCF** zostanie wyświetlony formularz i będzie on ładować się usługi.

2. W **klienta testowego WCF** formularza, kliknij dwukrotnie **GetData()** testowana metoda **IService1**. **GetData** pojawi się karta.

     ![GetData&#40; &#41; metoda](../data-tools/media/wcf4.png "wcf4")

3. W **żądania** wybierz opcję **wartość** pola i typu `Hello`.

     ![Pole wartości](../data-tools/media/wcf5.png "wcf5")

4. Kliknij przycisk **Invoke** przycisku. Jeśli **ostrzeżenie o zabezpieczeniach** zostanie wyświetlone okno dialogowe, kliknij przycisk **OK**. Wynik będzie wyświetlany na **odpowiedzi** pole.

     ![Wynik w polu odpowiedzi](../data-tools/media/wcf6.png "wcf6")

5. Na **pliku** menu, kliknij przycisk **zakończenia** aby zamknąć formularz testu.

## <a name="accessing-the-service"></a>Uzyskiwanie dostępu do usługi

#### <a name="to-reference-a-wcf-service"></a>Aby odwoływać się do usługi WCF

1. Na **pliku** menu wskaż **Dodaj** a następnie kliknij przycisk **nowy projekt**.

2. W **nowy projekt** okna dialogowego rozwiń **języka Visual Basic** lub **Visual C#** a następnie wybierz węzeł **Windows**, a następnie wybierz pozycję **Windows Forms aplikacji**. Kliknij przycisk **OK** otworzyć projektu.

     ![Projekt Windows Forms aplikacji](../data-tools/media/wcf7.png "wcf7")

3. Kliknij prawym przyciskiem myszy **WindowsApplication1** i kliknij przycisk **Dodaj odwołanie do usługi**. **Dodaj odwołanie do usługi** zostanie wyświetlone okno dialogowe.

4. W **Dodaj odwołanie do usługi** okno dialogowe, kliknij przycisk **odnajdź**.

     ![Okno dialogowe Dodaj odwołanie do usługi](../data-tools/media/wcf8.png "wcf8")

     **Service1** będą wyświetlane w **usług** okienka.

5. Kliknij przycisk **OK** można dodać odwołania do usługi.

#### <a name="to-build-a-client-application"></a>Tworzenie aplikacji klienckiej

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie **Form1.vb** lub **Form1.cs** otworzyć Windows Forms Designer, jeśli nie jest jeszcze otwarty.

2. Z **przybornika**, przeciągnij `TextBox` kontroli `Label` kontroli i `Button` formant na formularzu.

     ![Dodawanie formantów do formularza](../data-tools/media/wcf9.png "wcf9")

3. Kliknij dwukrotnie `Button`i Dodaj następujący kod w `Click` programu obsługi zdarzeń:

     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

4. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **WindowsApplication1** i kliknij przycisk **Ustaw jako projekt startowy**.

5. Naciśnij klawisz **F5** Aby uruchomić projekt. Wprowadź tekst, a następnie kliknij przycisk. Wyświetli etykietę "wprowadzona:" i wprowadzonego tekstu.

     ![Formularz jako wynik](../data-tools/media/wcf10.png "wcf10")

## <a name="see-also"></a>Zobacz też
 [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
