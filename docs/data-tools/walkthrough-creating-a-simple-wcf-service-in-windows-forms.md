---
title: Tworzenie prostej usługi WCF w Windows Forms
description: W tym instruktażu Utwórz usługę Windows Communication Foundation (WCF) w programie Visual Studio, przetestuj ją, a następnie uzyskaj dostęp do niej z poziomu aplikacji Windows Forms.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 5352ad4724e7c54e72dbaa52573c814657fa041e
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216101"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Przewodnik: tworzenie prostej usługi WCF w Windows Forms

W tym instruktażu pokazano, jak utworzyć prostą usługę Windows Communication Foundation (WCF), przetestować ją, a następnie uzyskać do niej dostęp z aplikacji Windows Forms.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-a-service"></a>Tworzenie usługi

1. Otwórz program Visual Studio.

::: moniker range="vs-2017"

2. W menu **plik** wybierz pozycję **Nowy** > **projekt**.

3. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual Basic** lub **Visual C#** , a następnie wybierz opcję **WCF**, a następnie pozycję **Biblioteka usług WCF**.

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

5. W **Eksplorator rozwiązań** kliknij dwukrotnie pozycję **IService1. vb** lub **IService1. cs**.

   ![Plik IService1](../data-tools/media/wcf2.png)

   Znajdź następujący wiersz:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1_2.cs" id="Snippet4":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1_2.vb" id="Snippet4":::

   Zmień typ `value` parametru na ciąg:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb" id="Snippet1":::

   W powyższym kodzie Zwróć uwagę `<OperationContract()>` na `[OperationContract]` atrybuty lub. Te atrybuty są wymagane dla każdej metody uwidocznionej przez usługę.

6. W **Eksplorator rozwiązań** kliknij dwukrotnie pozycję **Service1. vb** lub **Service1. cs**.

   ![Plik Service1](../data-tools/media/wcf3.png)

   Znajdź następujący wiersz:

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1_2.vb" id="Snippet5":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1_2.cs" id="Snippet5":::

   Zmień typ `value` parametru na ciąg:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs" id="Snippet2":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb" id="Snippet2":::

## <a name="test-the-service"></a>Testowanie usługi

1. Naciśnij klawisz **F5** , aby uruchomić usługę. Zostanie wyświetlony formularz **klienta testowego WCF** i zostanie załadowana usługa.

2. W formularzu **klienta testowego WCF** kliknij dwukrotnie metodę **GetData ()** w obszarze **IService1**. Zostanie wyświetlona karta **GetData** .

     ![Metoda GetData&#40;&#41; ](../data-tools/media/wcf4.png)

3. W polu **żądanie** wybierz pole **wartość** i wpisz `Hello` .

     ![Pole wartości](../data-tools/media/wcf5.png)

4. Kliknij przycisk **Wywołaj** . Jeśli pojawi się okno dialogowe **Ostrzeżenie o zabezpieczeniach** , kliknij przycisk **OK**. Wynik zostanie wyświetlony w polu **odpowiedź** .

     ![Wynik w polu odpowiedź](../data-tools/media/wcf6.png)

5. W menu **plik** kliknij polecenie **Zakończ** , aby zamknąć formularz testu.

## <a name="access-the-service"></a>Uzyskaj dostęp do usługi

### <a name="reference-the-wcf-service"></a>Odwoływanie się do usługi WCF

1. W menu **plik** wskaż polecenie **Dodaj** , a następnie kliknij pozycję **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual Basic** lub **Visual C#** , wybierz pozycję **Windows**, a następnie wybierz pozycję **aplikacja Windows Forms**. Kliknij przycisk **OK** , aby otworzyć projekt.

     ![Projekt Windows Forms aplikacji](../data-tools/media/wcf7.png)

3. Kliknij prawym przyciskiem myszy pozycję **WindowsApplication1** , a następnie kliknij pozycję **Dodaj odwołanie do usługi**. Zostanie wyświetlone okno dialogowe **Dodaj odwołanie do usługi** .

4. W **Dodaj odwołanie do usługi** okno dialogowe, kliknij przycisk **odkryj**.

     ![Okno dialogowe Dodaj odwołanie do usługi](../data-tools/media/wcf8.png)

     **Service1** jest wyświetlana w okienku **usługi** .

5. Kliknij przycisk **OK** , aby dodać odwołanie do usługi.

### <a name="build-a-client-application"></a>Tworzenie aplikacji klienckiej

1. W **Eksplorator rozwiązań** kliknij dwukrotnie przycisk **Form1. vb** lub **Form1. cs** , aby otworzyć Projektant formularzy systemu Windows, jeśli nie jest jeszcze otwarty.

2. Z **przybornika** przeciągnij `TextBox` kontrolkę, `Label` kontrolkę i `Button` kontrolkę na formularz.

     ![Dodawanie kontrolek do formularza](../data-tools/media/wcf9.png)

3. Kliknij dwukrotnie `Button` , a następnie Dodaj następujący kod do `Click` programu obsługi zdarzeń:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb" id="Snippet3":::

4. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **WindowsApplication1** , a następnie kliknij pozycję **Ustaw jako projekt startowy**.

5. Naciśnij klawisz **F5** , aby uruchomić projekt. Wprowadź tekst, a następnie kliknij przycisk. W etykiecie zostanie wyświetlona wartość "wprowadzono:" i zostanie wyświetlony wprowadzony tekst.

     ![Formularz pokazujący wynik](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Zobacz też

- [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
