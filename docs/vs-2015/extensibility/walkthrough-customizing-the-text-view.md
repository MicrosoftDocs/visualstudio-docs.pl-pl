---
title: 'Przewodnik: Dostosowywanie widoku tekstu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e96bb177d3cfa90b2c80304eabfd93d1bea76d5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202023"
---
# <a name="walkthrough-customizing-the-text-view"></a>Przewodnik: dostosowywanie widoku tekstu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok tekstu można dostosować, modyfikując dowolne z następujących właściwości w mapie formatu edytora:  
  
- Margines wskaźnika  
  
- Wstawianie karetki  
  
- Zastąp karetkę  
  
- Zaznaczony tekst  
  
- Nieaktywny zaznaczony tekst (oznacza to, że zaznaczony tekst ma utracony fokus)  
  
- Widoczne odstępy  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `ViewPropertyTest` .  
  
2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Usuń istniejące pliki klas.  
  
## <a name="defining-the-content-type"></a>Definiowanie typu zawartości  
  
1. Dodaj plik klasy i nadaj mu nazwę `ViewPropertyModifier` .  
  
2. Dodaj następujące `using` dyrektywy:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Zadeklaruj klasę o nazwie `TestViewCreationListener` , która dziedziczy z <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Wyeksportuj tę klasę o następujących atrybutach:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , aby określić typ zawartości, do której ma zastosowanie ten odbiornik.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Aby określić rolę tego odbiornika.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. W tej klasie zaimportuj <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Zmiana właściwości widoku  
  
1. Zaimplementuj <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodę, tak aby właściwości widoku były zmieniane po otwarciu widoku. Aby wprowadzić zmiany, najpierw Znajdź odpowiadający elementowi widoku, który <xref:System.Windows.ResourceDictionary> ma zostać znaleziony. Następnie zmień odpowiednią właściwość w słowniku zasobów i ustaw właściwości. Przetwarzanie wsadowe wywołań <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metody przez wywołanie <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metody przed ustawieniem właściwości, a następnie <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> po ustawieniu właściwości.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Kompilowanie i testowanie kodu  
  
1. Skompiluj rozwiązanie.  
  
     Po uruchomieniu tego projektu w debugerze tworzone jest drugie wystąpienie programu Visual Studio.  
  
2. Utwórz plik tekstowy i wpisz tekst.  
  
    - Karetka wstawiania powinna być amarantowa, a karetka zastępująca powinna być turkusowa.  
  
    - Margines wskaźnika (po lewej stronie widoku tekstu) powinien być jasnozielony.  
  
3. Zaznacz wpisany tekst. Kolor zaznaczonego tekstu powinien być jasny różowy.  
  
4. Gdy tekst jest zaznaczony, kliknij gdziekolwiek poza oknem tekstu. Kolor zaznaczonego tekstu powinien być ciemny różowy.  
  
5. Włącz widoczne odstępy. (W menu **Edycja** wskaż polecenie **Zaawansowane** , a następnie kliknij pozycję **Wyświetl biały znak**). Wpisz kilka kart w tekście. Czerwone strzałki reprezentujące karty powinny być wyświetlane.  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
