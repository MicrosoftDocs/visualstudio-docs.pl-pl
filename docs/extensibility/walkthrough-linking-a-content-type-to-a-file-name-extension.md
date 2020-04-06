---
title: 'Przewodnik: Łączenie typu zawartości z rozszerzeniem nazwy pliku | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 328be013b5d522938cd7450fc53d4866c632abb3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697090"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Instruktaż: łączenie typu zawartości z rozszerzeniem nazwy pliku
Można zdefiniować własny typ zawartości i połączyć rozszerzenie nazwy pliku do niego za pomocą edytora Managed Extensibility Framework (MEF) rozszerzenia. W niektórych przypadkach rozszerzenie nazwy pliku jest już zdefiniowane przez usługę języka. Ale, aby używać go z MEF, nadal należy połączyć go z typem zawartości.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Tworzenie projektu MEF

1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C# / Extensibility**, a następnie **VSIX Project**.) Nazwij `ContentTypeTest`rozwiązanie .

2. W pliku **source.extension.vsixmanifest** przejdź do karty **Zasoby** i ustaw pole **Typ** na **Microsoft.VisualStudio.MefComponent**, pole **Źródło** na Projekt w **bieżącym rozwiązaniu**i pole **Projekt** na nazwę projektu.

## <a name="define-the-content-type"></a>Definiowanie typu zawartości

1. Dodaj plik klasy i `FileAndContentTypes`nadaj jego nazwę .

2. Dodaj odwołania do następujących zestawów:

    1. System.componentmodel.composition

    2. Microsoft.VisualStudio.Text.Logic

    3. Microsoft.VisualStudio.CoreUtility

3. Dodaj następujące `using` dyrektywy.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. Deklaruj klasę statyczną, która zawiera definicje.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. W tej klasie <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> wyeksportuj nazwany "ukrył" i zadeklarować jego podstawową definicję jako "tekst".

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

- Aby zamapować ten typ zawartości na <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> rozszerzenie nazwy pliku, wyeksportuj rozszerzenie *.hid* i typ zawartości "ukrył".

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

1. Tworzenie rozszerzenia edytora. Na przykład można użyć rozszerzenia glifów marginesu opisanego w [przewodniku: Utwórz glif marginesu](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Dodaj klasę zdefiniowaną w tej procedurze.

3. Podczas eksportowania klasy rozszerzenia <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> dodaj do niej typ "ukrył".

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Zobacz też
- [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
