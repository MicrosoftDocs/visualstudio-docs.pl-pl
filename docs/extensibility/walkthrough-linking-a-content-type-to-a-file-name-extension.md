---
title: 'Przewodnik: Łączenie typu zawartości z rozszerzeniem nazwy pliku | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16f3a33ff273b62c701eae66d8fda1ff7178c5c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965044"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Przewodnik: Połączyć typu zawartości z rozszerzeniem nazwy pliku
Można zdefiniować typu zawartości i połączyć rozszerzenie nazwy pliku przy użyciu rozszerzenia Managed Extensibility Framework (MEF) edytora. W niektórych przypadkach rozszerzenie nazwy pliku jest już zdefiniowany przez usługę języka. Jednak aby używać go z MEF, nadal należy połączyć go z typem zawartości.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie instaluj programu Visual Studio SDK z Centrum pobierania. Został on uwzględniony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Utwórz projekt MEF

1. Utwórz projekt VSIX języka C#. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projekt VSIX**.) Nazwij rozwiązanie `ContentTypeTest`.

2. W **source.extension.vsixmanifest** pliku, przejdź do **zasoby** , a następnie ustaw **typu** pole **Microsoft.VisualStudio.MefComponent**, **źródła** pole **projekt w bieżącym rozwiązaniu**i **projektu** pola Nazwa projektu.

## <a name="define-the-content-type"></a>Zdefiniowanie typu zawartości

1. Dodaj plik klasy i nadaj mu nazwę `FileAndContentTypes`.

2. Dodaj odwołania do następujących zestawów:

    1. System.ComponentModel.Composition

    2. Microsoft.VisualStudio.Text.Logic

    3. Microsoft.VisualStudio.CoreUtility

3. Dodaj następujący kod `using` dyrektywy.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. Deklarowanie klasy statycznej, który zawiera definicje.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. W tej klasie wyeksportować <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> o nazwie "hid" i deklarujemy jego podstawową definicję jako "text".

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>Łączenie z rozszerzeniem nazwy pliku do typu zawartości

- Aby zamapować tego typu zawartości na rozszerzenie nazwy pliku, należy wyeksportować <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> zawierający rozszerzenia *HID* i typu zawartości "hid".

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

## <a name="add-the-content-type-to-an-editor-export"></a>Dodaj typ zawartości do edytora eksportowanie

1. Tworzenie rozszerzenia edytora. Na przykład, można użyć rozszerzenia symbol margines opisanego w [instruktażu: Utwórz marginesie](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Dodaj klasę, które zostały zdefiniowane w tej procedurze.

3. Podczas eksportowania klasy rozszerzenia, Dodaj <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> typu "hid" do niego.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Zobacz także
- [Punkty rozszerzenia usługi oraz edytora języka](../extensibility/language-service-and-editor-extension-points.md)