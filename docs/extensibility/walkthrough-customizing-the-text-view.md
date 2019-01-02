---
title: 'Przewodnik: Dostosowywanie widoku tekstu | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8748ccade8e610c66d9c4142312c2c5dfed1ddf9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917322"
---
# <a name="walkthrough-customize-the-text-view"></a>Przewodnik: Dostosowywanie widoku tekstu
Widok tekstu można dostosować, zmieniając dowolne z następujących właściwości w mapie jego format edytora:  
  
-   Margines wskaźnika  
  
-   Daszek wstawiania  
  
-   Zastąp karetki  
  
-   Zaznaczony tekst  
  
-   Nieaktywny zaznaczony tekst (czyli zaznaczonego tekstu, który utraciła fokus)  
  
-   Widoczne odstępy  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Został on uwzględniony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Utwórz projekt MEF  
  
1.  Utwórz projekt VSIX języka C#. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projekt VSIX**.) Nazwij rozwiązanie `ViewPropertyTest`.  
  
2.  Dodaj szablon elementu edytora klasyfikatora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Usuń istniejące pliki klasy.  
  
## <a name="define-the-content-type"></a>Zdefiniowanie typu zawartości  
  
1. Dodaj plik klasy i nadaj mu nazwę `ViewPropertyModifier`.  
  
2. Dodaj następujący kod `using` dyrektywy:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3. Zadeklaruj klasę o nazwie `TestViewCreationListener` tej, która dziedziczy <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Eksportuj tej klasy, z następującymi atrybutami:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Aby określić typ zawartości, do której stosują się tego odbiornika.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Aby określić roli tego odbiornika.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4. W tej klasie zaimportować <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="change-the-view-properties"></a>Zmień właściwości widoku  
  
1.  Konfigurowanie <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metody, aby właściwości widoku zostaną zmienione po otwarciu widoku. Aby wprowadzić zmianę, najpierw Znajdź <xref:System.Windows.ResourceDictionary> , który odpowiada aspekt widoku, którą chcesz znaleźć. Następnie należy zmienić odpowiednie właściwości w słowniku zasobów i ustaw właściwości. Batch wywołania <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metoda przez wywołanie metody <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metoda przed ustawieniem właściwości i następnie <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> po ustawieniu właściwości.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu  
  
1.  Skompiluj rozwiązanie.  
  
     Po uruchomieniu tego projektu w debugerze, drugie wystąpienie programu Visual Studio został uruchomiony.  
  
2.  Utwórz plik tekstowy i wpisz jakiś tekst.  
  
    -   Daszek wstawiania powinny być amarantowy i karetki zastępowania powinna być turkusowy.  
  
    -   Margines wskaźnika (po lewej stronie widoku tekstu) powinna być światła zielony.  
  
3.  Wybierz wpisany tekst. Kolor tekstu zaznaczonego powinny być światła różowy.  
  
4.  Gdy tekst jest zaznaczony, kliknij w dowolnym miejscu poza okna tekstowego. Kolor tekstu zaznaczonego powinna być ciemny róż.  
  
5.  Włącz widoczne białe znaki. (Na **Edytuj** menu wskaż **zaawansowane** a następnie kliknij przycisk **Wyświetl białe znaki**). Niektóre karty można wpisać tekst. Czerwone strzałki, które reprezentują kart powinna być wyświetlana.  
  
## <a name="see-also"></a>Zobacz także  
 [Punkty rozszerzenia usługi oraz edytora języka](../extensibility/language-service-and-editor-extension-points.md)