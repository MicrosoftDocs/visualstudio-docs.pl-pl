---
title: 'Przewodnik: Dostosowywanie widoku tekstu | Microsoft Docs'
description: Dowiedz się, jak dostosować widok tekstowy, modyfikując dowolne z kilku właściwości w mapie formatu edytora, korzystając z tego przewodnika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5ef4d0b408afc00a806e73d1e2eae7a07dde7814
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216855"
---
# <a name="walkthrough-customize-the-text-view"></a>Przewodnik: Dostosowywanie widoku tekstu
Widok tekstu można dostosować, modyfikując dowolne z następujących właściwości w mapie formatu edytora:

- Margines wskaźnika

- Wstawianie karetki

- Zastąp karetkę

- Zaznaczony tekst

- Nieaktywny zaznaczony tekst (czyli zaznaczony tekst, który utracił fokus)

- Widoczne odstępy

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dołączana jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Tworzenie projektu MEF

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `ViewPropertyTest` .

2. Dodaj szablon elementu klasyfikatora edytora do projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Usuń istniejące pliki klas.

## <a name="define-the-content-type"></a>Zdefiniuj typ zawartości

1. Dodaj plik klasy i nadaj mu nazwę `ViewPropertyModifier` .

2. Dodaj następujące `using` dyrektywy:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet1":::

3. Zadeklaruj klasę o nazwie `TestViewCreationListener` , która dziedziczy z <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Wyeksportuj tę klasę o następujących atrybutach:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> , aby określić typ zawartości, do której ma zastosowanie ten odbiornik.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Aby określić rolę tego odbiornika.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet2":::

4. W tej klasie zaimportuj <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet3":::

## <a name="change-the-view-properties"></a>Zmień właściwości widoku

1. Skonfiguruj <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodę tak, aby właściwości widoku były zmieniane po otwarciu widoku. Aby wprowadzić zmiany, najpierw Znajdź odpowiadający elementowi widoku, który <xref:System.Windows.ResourceDictionary> ma zostać znaleziony. Następnie zmień odpowiednią właściwość w słowniku zasobów i ustaw właściwości. Przetwarzanie wsadowe wywołań <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metody przez wywołanie <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metody przed ustawieniem właściwości, a następnie <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> po ustawieniu właściwości.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet4":::

## <a name="build-and-test-the-code"></a>Kompiluj i Testuj kod

1. Skompiluj rozwiązanie.

     Po uruchomieniu tego projektu w debugerze uruchomione jest drugie wystąpienie programu Visual Studio.

2. Utwórz plik tekstowy i wpisz tekst.

    - Karetka wstawiania powinna być amarantowa, a karetka zastępująca powinna być turkusowa.

    - Margines wskaźnika (po lewej stronie widoku tekstu) powinien być jasnozielony.

3. Zaznacz wpisany tekst. Kolor zaznaczonego tekstu powinien być jasny różowy.

4. Gdy tekst jest zaznaczony, kliknij gdziekolwiek poza oknem tekstu. Kolor zaznaczonego tekstu powinien być ciemny różowy.

5. Włącz widoczne odstępy. (W menu **Edycja** wskaż polecenie **Zaawansowane** , a następnie kliknij pozycję **Wyświetl biały znak**). Wpisz kilka kart w tekście. Czerwone strzałki reprezentujące karty powinny być wyświetlane.

## <a name="see-also"></a>Zobacz też
- [Punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
