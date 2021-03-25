---
title: Łączenie typu zawartości z rozszerzeniem nazwy pliku
description: Dowiedz się, jak połączyć własny typ zawartości z rozszerzeniem nazwy pliku przy użyciu edytora Managed Extensibility Framework rozszerzenia w tym instruktażu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 990f10fe82b9230c12ba13d736750f2f644c3ee5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078451"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku
Można zdefiniować własny typ zawartości i połączyć z nim rozszerzenie nazwy pliku przy użyciu rozszerzeń edytora Managed Extensibility Framework (MEF). W niektórych przypadkach rozszerzenie nazwy pliku jest już zdefiniowane przez usługę języka. Jednak aby użyć go z MEF, należy nadal połączyć go z typem zawartości.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dołączana jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Tworzenie projektu MEF

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `ContentTypeTest` .

2. W pliku **source. Extension. vsixmanifest** przejdź do karty **zasoby** , a następnie ustaw pole **Typ** na **Microsoft. VisualStudio. MefComponent**, pole **Źródło** **w projekcie w bieżącym rozwiązaniu**, a pole **projektu** na nazwę projektu.

## <a name="define-the-content-type"></a>Zdefiniuj typ zawartości

1. Dodaj plik klasy i nadaj mu nazwę `FileAndContentTypes` .

2. Dodaj odwołania do następujących zestawów:

    1. System. ComponentModel. kompozycji

    2. Microsoft. VisualStudio. Text. Logic

    3. Microsoft. VisualStudio. CoreUtility

3. Dodaj następujące `using` dyrektywy.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. Zadeklaruj klasę statyczną, która zawiera definicje.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. W tej klasie należy wyeksportować <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> nazwany "HID" i zadeklarować jego definicję podstawową jako "text".

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>Łączenie rozszerzenia nazwy pliku z typem zawartości

- Aby zmapować ten typ zawartości na rozszerzenie nazwy pliku, należy wyeksportować element, <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> który ma rozszerzenie *. HID* i typ zawartości "HID".

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
         [Export]
         [Name("hid")]
         [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;

         [Export]
         [FileExtension(".hid")]
         [ContentType("hid")]
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;
    }
    ```

## <a name="add-the-content-type-to-an-editor-export"></a>Dodawanie typu zawartości do eksportu edytora

1. Utwórz rozszerzenie edytora. Na przykład można użyć rozszerzenia symbolu marginesu opisanego w [przewodniku: Utwórz symbol marginesu](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Dodaj klasę zdefiniowaną w tej procedurze.

3. Podczas eksportowania klasy rozszerzeń należy dodać <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> do niej typ "HID".

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Zobacz też
- [Punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
