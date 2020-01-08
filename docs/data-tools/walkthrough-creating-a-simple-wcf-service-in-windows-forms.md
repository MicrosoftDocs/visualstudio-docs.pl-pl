---
title: 'Przewodnik: tworzenie prostej usługi WCF w Windows Forms'
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3d3f2e80ff3e2b94c46d1e2658c40bccf2e6c365
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586019"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Przewodnik: tworzenie prostej usługi WCF w Windows Forms

W tym instruktażu pokazano, jak utworzyć prostą usługę Windows Communication Foundation (WCF), przetestować ją, a następnie uzyskać do niej dostęp z aplikacji Windows Forms.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-a-service"></a>Tworzenie usługi

1. Otwórz program Visual Studio.

::: moniker range="vs-2017"

2. W menu **plik** wybierz **Nowy** **projekt**>.

3. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual Basic** lub **element wizualny C#**  , a następnie wybierz opcję **WCF**, a następnie pozycję **Biblioteka usług WCF**.

4. Kliknij przycisk **OK**, aby utworzyć projekt.

   ![Projekt biblioteki usługi WCF](../data-tools/media/wcf1.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

3. W polu wyszukiwania na stronie **Utwórz nowy projekt** wpisz **bibliotekę usług WCF** . Wybierz szablon C# lub Visual Basic dla **biblioteki usługi WCF**, a następnie kliknij przycisk **dalej**.

   ![Utwórz nowy projekt biblioteki usługi WCF w programie Visual Studio 2019](media/vs-2019/create-new-wcf-service-library.png)

   > [!TIP]
   > Jeśli nie widzisz żadnych szablonów, może być konieczne zainstalowanie składnika **Windows Communication Foundation** programu Visual Studio. Wybierz pozycję **Zainstaluj więcej narzędzi i funkcji** , aby otworzyć Instalator programu Visual Studio. Wybierz kartę **poszczególne składniki** , przewiń w dół do obszarze **działania deweloperskie**, a następnie wybierz pozycję **Windows Communication Foundation**. Kliknij przycisk **Modyfikuj**.

4. Na stronie **Konfigurowanie nowego projektu** kliknij przycisk **Utwórz**.

::: moniker-end

   > [!NOTE]
   > Spowoduje to utworzenie usługi działającej, która może być testowana i dostępna. W poniższych dwóch krokach pokazano, jak można zmodyfikować domyślną metodę, aby użyć innego typu danych. W rzeczywistej aplikacji należy również dodać własne funkcje do usługi.

5. W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję **IService1. vb** lub **IService1.cs**.

   ![Plik IService1](../data-tools/media/wcf2.png)

   Znajdź następujący wiersz:

   [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
   [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

   Zmień typ parametru `value` na ciąg:

   [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
   [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

   W powyższym kodzie Zwróć uwagę na atrybuty `<OperationContract()>` lub `[OperationContract]`. Te atrybuty są wymagane dla każdej metody uwidocznionej przez usługę.

6. W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję **Service1. vb** lub **Service1.cs**.

   ![Plik Service1](../data-tools/media/wcf3.png)

   Znajdź następujący wiersz:

   [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
   [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

   Zmień typ parametru `value` na ciąg:

   [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
   [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Testowanie usługi

1. Naciśnij klawisz **F5** , aby uruchomić usługę. Zostanie wyświetlony formularz **klienta testowego WCF** i zostanie załadowana usługa.

2. W formularzu **klienta testowego WCF** kliknij dwukrotnie metodę **GetData ()** w obszarze **IService1**. Zostanie wyświetlona karta **GetData** .

     ![Metoda GetData&#40; &#41;](../data-tools/media/wcf4.png)

3. W polu **żądanie** wybierz pole **wartość** i wpisz `Hello`.

     ![Pole wartości](../data-tools/media/wcf5.png)

4. Kliknij przycisk **Wywołaj** . Jeśli pojawi się okno dialogowe **Ostrzeżenie o zabezpieczeniach** , kliknij przycisk **OK**. Wynik zostanie wyświetlony w polu **odpowiedź** .

     ![Wynik w polu odpowiedź](../data-tools/media/wcf6.png)

5. W menu **plik** kliknij polecenie **Zakończ** , aby zamknąć formularz testu.

## <a name="access-the-service"></a>Uzyskaj dostęp do usługi

### <a name="reference-the-wcf-service"></a>Odwoływanie się do usługi WCF

1. W menu **plik** wskaż polecenie **Dodaj** , a następnie kliknij pozycję **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual Basic** lub **wizualizacji C#**  , wybierz pozycję **Windows**, a następnie wybierz pozycję **aplikacja Windows Forms**. Kliknij przycisk **OK** , aby otworzyć projekt.

     ![Projekt Windows Forms aplikacji](../data-tools/media/wcf7.png)

3. Kliknij prawym przyciskiem myszy pozycję **WindowsApplication1** , a następnie kliknij pozycję **Dodaj odwołanie do usługi**. Zostanie wyświetlone okno dialogowe **Dodaj odwołanie do usługi** .

4. W **Dodaj odwołanie do usługi** okno dialogowe, kliknij przycisk **odkryj**.

     ![Okno dialogowe Dodaj odwołanie do usługi](../data-tools/media/wcf8.png)

     **Service1** jest wyświetlana w okienku **usługi** .

5. Kliknij przycisk **OK** , aby dodać odwołanie do usługi.

### <a name="build-a-client-application"></a>Tworzenie aplikacji klienckiej

1. W **Eksplorator rozwiązań**kliknij dwukrotnie przycisk **Form1. vb** lub **Form1.cs** , aby otworzyć Projektant formularzy systemu Windows, jeśli nie jest jeszcze otwarty.

2. Z **przybornika**przeciągnij kontrolkę `TextBox`, kontrolkę `Label` i kontrolkę `Button` na formularz.

     ![Dodawanie kontrolek do formularza](../data-tools/media/wcf9.png)

3. Kliknij dwukrotnie `Button`i Dodaj następujący kod do programu obsługi zdarzeń `Click`:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **WindowsApplication1** , a następnie kliknij pozycję **Ustaw jako projekt startowy**.

5. Naciśnij klawisz **F5** , aby uruchomić projekt. Wprowadź tekst, a następnie kliknij przycisk. W etykiecie zostanie wyświetlona wartość "wprowadzono:" i zostanie wyświetlony wprowadzony tekst.

     ![Formularz pokazujący wynik](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Zobacz także

- [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
