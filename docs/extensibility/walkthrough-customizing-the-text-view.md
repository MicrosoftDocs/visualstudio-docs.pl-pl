---
title: 'Przewodnik: Dostosowywanie widoku tekstu | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d99f9201761bbe079c34ccf61339158863509dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697468"
---
# <a name="walkthrough-customize-the-text-view"></a>Instruktaż: dostosowywanie widoku tekstu
Widok tekstu można dostosować, modyfikując dowolną z następujących właściwości na mapie w formacie edytora:

- Margines wskaźnika

- Wkładanie cieszy

- Zastępowanie cieczy

- Zaznaczony tekst

- Nieaktywny zaznaczony tekst (czyli zaznaczony tekst, który utracił fokus)

- Widoczne odstępy

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Tworzenie projektu MEF

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C# / Extensibility**, a następnie **VSIX Project**.) Nazwij `ViewPropertyTest`rozwiązanie .

2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

## <a name="define-the-content-type"></a>Definiowanie typu zawartości

1. Dodaj plik klasy i `ViewPropertyModifier`nadaj jego nazwę .

2. Dodaj następujące `using` dyrektywy:

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. Deklaruj klasę o nazwie, `TestViewCreationListener` która dziedziczy po <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Wyeksportuj tę klasę z następującymi atrybutami:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, aby określić typ zawartości, do której stosuje się ten odbiornik.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>, aby określić rolę tego odbiornika.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. W tej klasie <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>zaimportuj plik .

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>Zmienianie właściwości widoku

1. Skonfiguruj <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodę tak, aby właściwości widoku były zmieniane po otwarciu widoku. Aby wprowadzić zmianę, najpierw <xref:System.Windows.ResourceDictionary> znajdź ten, który odpowiada aspektowi widoku, który chcesz znaleźć. Następnie zmień odpowiednią właściwość w słowniku zasobów i ustaw właściwości. Partia wywołania <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metody, wywołując <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metodę przed ustawieniem właściwości, <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> a następnie po ustawieniu właściwości.

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>Tworzenie i testowanie kodu

1. Skompiluj rozwiązanie.

     Po uruchomieniu tego projektu w debugerze zostanie uruchomione drugie wystąpienie programu Visual Studio.

2. Utwórz plik tekstowy i wpisz tekst.

    - Wkładka powinna być purpurowa, a nadpisywowa powinna być turkusowa.

    - Margines wskaźnika (po lewej stronie widoku tekstu) powinien być jasnozielony.

3. Zaznacz wpisany tekst. Kolor zaznaczonego tekstu powinien być jasnoróżowy.

4. Gdy tekst jest zaznaczony, kliknij dowolne miejsce poza oknem tekstowym. Kolor zaznaczonego tekstu powinien być ciemnoróżowy.

5. Włącz widoczne odstępy. (W menu **Edycja** wskaż polecenie **Zaawansowane,** a następnie kliknij polecenie **Wyświetl biały spację).** Wpisz kilka kart w tekście. Powinny być wyświetlane czerwone strzałki reprezentujące karty.

## <a name="see-also"></a>Zobacz też
- [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
