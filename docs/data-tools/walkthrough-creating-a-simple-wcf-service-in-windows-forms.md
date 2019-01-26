---
title: 'Przewodnik: Tworzenie prostą usługę WCF w formularzach Windows Forms'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 74643d6511fc0eac99eff9693eac9cb9234df88f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966260"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Przewodnik: Utwórz prostą usługę WCF w formularzach Windows Forms

W tym instruktażu przedstawiono sposób tworzenia prostej [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] usługi, testowania i do niego dostęp z aplikacji Windows Forms.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-the-service"></a>Tworzenie usługi

### <a name="to-create-a-wcf-service"></a>Tworzenie usługi WCF

1.  Na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.

2.  W **nowy projekt** okna dialogowego rozwiń **języka Visual Basic** lub **Visual C#** węzła i kliknij przycisk **WCF**, a następnie **WCF Biblioteka usługi**. Kliknij przycisk **OK** otworzyć projektu.

     ![Projekt biblioteki usługi WCF](../data-tools/media/wcf1.png)

    > [!NOTE]
    >  Spowoduje to utworzenie usługi pracy, przetestowane i używanych. Następujące dwa kroki pokazują, jak może zmodyfikować domyślną metodę, aby użyć innego typu danych. W rzeczywistej aplikacji należy również dodać własne funkcje do usługi.

3.  ![Plik IService1](../data-tools/media/wcf2.png)

     W **Eksploratora rozwiązań**, kliknij dwukrotnie **IService1.vb** lub **IService1.cs** i znajdź następujący wiersz:

     [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
     [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

     Zmień typ `value` parametr na ciąg:

     [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
     [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

     W powyższym kodzie, należy pamiętać, `<OperationContract()>` lub `[OperationContract]` atrybutów. Te atrybuty są wymagane do dowolnej metody udostępnianych przez usługę.

4.  ![Plik Service1](../data-tools/media/wcf3.png)

     W **Eksploratora rozwiązań**, kliknij dwukrotnie **Service1.vb** lub **Service1.cs** i znajdź następujący wiersz:

     [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
     [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

     Zmień typ `value` parametr na ciąg:

     [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
     [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Testowanie usługi

### <a name="to-test-a-wcf-service"></a>Aby przetestować usługę WCF

1.  Naciśnij klawisz **F5** do uruchamiania usługi. A **klienta testowego WCF** formularza zostanie wyświetlony i ładuje usługę.

2.  W **klienta testowego WCF** formularza, kliknij dwukrotnie **GetData()** testowana metoda **IService1**. **GetData** zostanie wyświetlona karta.

     ![GetData&#40; &#41; — metoda](../data-tools/media/wcf4.png)

3.  W **żądania** wybierz opcję **wartość** pola i typu `Hello`.

     ![Pole wartości](../data-tools/media/wcf5.png)

4.  Kliknij przycisk **Invoke** przycisku. Jeśli **ostrzeżenie o zabezpieczeniach** pojawi się okno dialogowe, kliknij przycisk **OK**. Wyświetla wynik **odpowiedzi** pole.

     ![Wynik w polu odpowiedzi](../data-tools/media/wcf6.png)

5.  Na **pliku** menu, kliknij przycisk **zakończenia** aby zamknąć formularz testu.

## <a name="access-the-service"></a>Dostęp do usługi

### <a name="to-reference-a-wcf-service"></a>Aby odwoływać się do usługi WCF

1.  Na **pliku** menu wskaż **Dodaj** a następnie kliknij przycisk **nowy projekt**.

2.  W **nowy projekt** okna dialogowego rozwiń **języka Visual Basic** lub **Visual C#**  węzła, wybierz opcję **Windows**, a następnie wybierz pozycję  **Windows Forms aplikacji**. Kliknij przycisk **OK** otworzyć projektu.

     ![Projekt Windows Forms aplikacji](../data-tools/media/wcf7.png)

3.  Kliknij prawym przyciskiem myszy **WindowsApplication1** i kliknij przycisk **Dodaj odwołanie do usługi**. **Dodaj odwołanie do usługi** pojawi się okno dialogowe.

4.  W **Dodaj odwołanie do usługi** okno dialogowe, kliknij przycisk **odnajdź**.

     ![Okno dialogowe Dodaj odwołanie do usługi](../data-tools/media/wcf8.png)

     **Service1** Wyświetla **usług** okienka.

5.  Kliknij przycisk **OK** można dodać odwołania do usługi.

### <a name="to-build-a-client-application"></a>Tworzenie aplikacji klienckiej

1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **Form1.vb** lub **Form1.cs** otworzyć Windows Forms Designer, jeśli nie jest jeszcze otwarty.

2.  Z **przybornika**, przeciągnij `TextBox` kontroli `Label` kontroli i `Button` formant na formularzu.

     ![Dodawanie formantów do formularza](../data-tools/media/wcf9.png)

3.  Kliknij dwukrotnie `Button`i Dodaj następujący kod w `Click` programu obsługi zdarzeń:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **WindowsApplication1** i kliknij przycisk **Ustaw jako projekt startowy**.

5.  Naciśnij klawisz **F5** Aby uruchomić projekt. Wprowadź tekst, a następnie kliknij przycisk. Wyświetla etykietę "wprowadzona:" i pokazuje tekst wprowadzony.

     ![Formularz jako wynik](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Zobacz także

- [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)