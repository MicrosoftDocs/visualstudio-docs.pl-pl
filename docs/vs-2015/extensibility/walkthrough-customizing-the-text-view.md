---
title: 'Wskazówki: Dostosowywanie widoku tekstu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 38cbd0117f5f49666ee5da42d0f60dadf451ffda
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781819"
---
# <a name="walkthrough-customizing-the-text-view"></a>Przewodnik: dostosowywanie widoku tekstu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok tekstu można dostosować, zmieniając dowolne z następujących właściwości w mapie jego format edytora:  
  
-   Margines wskaźnika  
  
-   Daszek wstawiania  
  
-   Zastąp karetki  
  
-   Zaznaczony tekst  
  
-   Nieaktywny zaznaczony tekst (czyli zaznaczonego tekstu, który utraciła fokus)  
  
-   Widoczne odstępy  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
1.  Utwórz projekt VSIX języka C#. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projekt VSIX**.) Nazwij rozwiązanie `ViewPropertyTest`.  
  
2.  Dodaj szablon elementu edytora klasyfikatora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń istniejące pliki klasy.  
  
## <a name="defining-the-content-type"></a>Definiowanie typu zawartości  
  
1. Dodaj plik klasy i nadaj mu nazwę `ViewPropertyModifier`.  
  
2. Dodaj następujący kod `using` dyrektywy:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Zadeklaruj klasę o nazwie `TestViewCreationListener` tej, która dziedziczy <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Eksportuj tej klasy, z następującymi atrybutami:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Aby określić typ zawartości, do której stosują się tego odbiornika.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Aby określić roli tego odbiornika.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. W tej klasie zaimportować <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Zmiana właściwości widoku  
  
1.  Implementowanie <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metody, aby właściwości widoku zostaną zmienione po otwarciu widoku. Aby wprowadzić zmianę, najpierw Znajdź <xref:System.Windows.ResourceDictionary> , który odpowiada aspekt widoku, którą chcesz znaleźć. Zmień właściwość odpowiednie w słowniku zasobów, a następnie ustaw właściwości. Batch wywołania <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metoda przez wywołanie metody <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metoda przed ustawieniem właściwości i następnie <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> po ustawieniu właściwości.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Tworzenie i testowanie kodu  
  
1.  Skompiluj rozwiązanie.  
  
     Po uruchomieniu tego projektu w debugerze drugiego wystąpienia programu Visual Studio jest uruchomiony.  
  
2.  Utwórz plik tekstowy i wpisz jakiś tekst.  
  
    -   Daszek wstawiania powinny być amarantowy i karetki zastępowania powinna być turkusowy.  
  
    -   Margines wskaźnika (po lewej stronie widoku tekstu) powinna być światła zielony.  
  
3.  Zaznacz tekst, który został wpisany. Kolor tekstu zaznaczonego powinny być światła różowy.  
  
4.  Gdy tekst jest zaznaczony, kliknij w dowolnym miejscu poza okna tekstowego. Kolor tekstu zaznaczonego powinna być ciemny róż.  
  
5.  Włącz widoczne białe znaki. (Na **Edytuj** menu wskaż **zaawansowane** a następnie kliknij przycisk **Wyświetl białe znaki**). Niektóre karty można wpisać tekst. Czerwone strzałki, które reprezentują kart powinna być wyświetlana.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)

