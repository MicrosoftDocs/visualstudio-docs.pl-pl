---
title: 'Przewodnik: tworzenie prostej usługi WCF w Windows Forms | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 366567a13ad23ab19ffd88f19997b92025abe952
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671080"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>Przewodnik: tworzenie prostej usługi WCF w Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak utworzyć prostą usługę [!INCLUDE[vsindigo](../includes/vsindigo-md.md)], przetestować ją, a następnie uzyskać do niej dostęp z poziomu aplikacji Windows Forms.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="creating-the-service"></a>Tworzenie usługi

#### <a name="to-create-a-wcf-service"></a>Aby utworzyć usługę WCF

1. W menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual Basic** lub **element wizualny C#**  , a następnie kliknij opcję **WCF**, a następnie pozycję **Biblioteka usług WCF**. Kliknij przycisk **OK** , aby otworzyć projekt.

     ![Projekt biblioteki usługi WCF](../data-tools/media/wcf1.PNG "wcf1")

    > [!NOTE]
    > Spowoduje to utworzenie usługi działającej, która może być testowana i dostępna. W poniższych dwóch krokach pokazano, jak można zmodyfikować domyślną metodę, aby użyć innego typu danych. W rzeczywistej aplikacji należy również dodać własne funkcje do usługi.

3. ![Plik IService1](../data-tools/media/wcf2.png "wcf2")

     W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję IService1. vb lub IService1.cs i znajdź następujący wiersz:

     [!code-csharp[WCFWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1_2.cs#4)]
     [!code-vb[WCFWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1_2.vb#4)]

     Zmień typ parametru `value` na `String`:

     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

     W powyższym kodzie Zwróć uwagę na atrybuty `<OperationContract()>` lub `[OperationContract]`. Te atrybuty są wymagane dla każdej metody uwidocznionej przez usługę.

4. ![Plik Service1](../data-tools/media/wcf3.png "wcf3")

     W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję Service1. vb lub Service1.cs i znajdź następujący wiersz:

     [!code-csharp[WCFWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1_2.cs#5)]
     [!code-vb[WCFWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1_2.vb#5)]

     Zmień typ parametru Value na `String`:

     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]

## <a name="testing-the-service"></a>Testowanie usługi

#### <a name="to-test-a-wcf-service"></a>Aby przetestować usługę WCF

1. Naciśnij klawisz **F5** , aby uruchomić usługę. Zostanie wyświetlony formularz **klienta testowego WCF** i zostanie załadowana usługa.

2. W formularzu **klienta testowego WCF** kliknij dwukrotnie metodę **GetData ()** w obszarze **IService1**. Zostanie wyświetlona karta **GetData** .

     ![Metoda GetData&#40; &#41;](../data-tools/media/wcf4.png "wcf4")

3. W polu **żądanie** wybierz pole **wartość** i wpisz `Hello`.

     ![Pole wartości](../data-tools/media/wcf5.png "wcf5")

4. Kliknij przycisk **Wywołaj** . Jeśli zostanie wyświetlone okno dialogowe **Ostrzeżenie o zabezpieczeniach** , kliknij przycisk **OK**. W polu **odpowiedź** zostanie wyświetlony wynik.

     ![Wynik w polu odpowiedź](../data-tools/media/wcf6.png "wcf6")

5. W menu **plik** kliknij polecenie **Zakończ** , aby zamknąć formularz testu.

## <a name="accessing-the-service"></a>Uzyskiwanie dostępu do usługi

#### <a name="to-reference-a-wcf-service"></a>Aby odwołać się do usługi WCF

1. W menu **plik** wskaż polecenie **Dodaj** , a następnie kliknij pozycję **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual Basic** lub **element wizualny C#**  , a następnie wybierz pozycję **Windows**, a następnie wybierz pozycję **aplikacja Windows Forms**. Kliknij przycisk **OK** , aby otworzyć projekt.

     ![Projekt Windows Forms aplikacji](../data-tools/media/wcf7.png "wcf7")

3. Kliknij prawym przyciskiem myszy pozycję **WindowsApplication1** , a następnie kliknij pozycję **Dodaj odwołanie do usługi**. Zostanie wyświetlone okno dialogowe **Dodaj odwołanie do usługi** .

4. W **Dodaj odwołanie do usługi** okno dialogowe, kliknij przycisk **odkryj**.

     ![Okno dialogowe Dodaj odwołanie do usługi](../data-tools/media/wcf8.png "wcf8")

     **Service1** zostanie wyświetlona w okienku **usługi** .

5. Kliknij przycisk **OK** , aby dodać odwołanie do usługi.

#### <a name="to-build-a-client-application"></a>Aby skompilować aplikację kliencką

1. W **Eksplorator rozwiązań**kliknij dwukrotnie przycisk **Form1. vb** lub **Form1.cs** , aby otworzyć Projektant formularzy systemu Windows, jeśli nie jest jeszcze otwarty.

2. Z **przybornika**przeciągnij kontrolkę `TextBox`, kontrolkę `Label` i kontrolkę `Button` na formularz.

     ![Dodawanie kontrolek do formularza](../data-tools/media/wcf9.png "wcf9")

3. Kliknij dwukrotnie `Button` i Dodaj następujący kod do programu obsługi zdarzeń `Click`:

     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

4. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **WindowsApplication1** , a następnie kliknij pozycję **Ustaw jako projekt startowy**.

5. Naciśnij klawisz **F5** , aby uruchomić projekt. Wprowadź tekst, a następnie kliknij przycisk. Etykieta zostanie wyświetlona "wprowadzona wartość:" i wprowadzony tekst.

     ![Formularz pokazujący wynik](../data-tools/media/wcf10.png "wcf10")

## <a name="see-also"></a>Zobacz też
 [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
