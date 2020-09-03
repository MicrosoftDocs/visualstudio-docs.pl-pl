---
title: 'Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: beae9d0526cb9f2f294f2267a8da52d3ce3d8c08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201994"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Przewodnik: łączenie typu zawartości z rozszerzeniem nazwy pliku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zdefiniować własny typ zawartości i połączyć z nim rozszerzenie nazwy pliku za pomocą rozszerzeń edytora Managed Extensibility Framework (MEF). W niektórych przypadkach rozszerzenie nazwy pliku zostało już zdefiniowane przez usługę języka; Niemniej jednak, aby używać go z MEF, nadal musisz połączyć go z typem zawartości.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
1. Utwórz projekt VSIX języka C#. (W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#/rozszerzalność**, a następnie **Projekt VSIX**). Nadaj nazwę rozwiązanie `ContentTypeTest` .  
  
2. W pliku **source. Extension. vsixmanifest** przejdź do karty **zasoby** , a następnie ustaw pole **Typ** na **Microsoft. VisualStudio. MefComponent**, pole **Źródło** **w projekcie w bieżącym rozwiązaniu**, a pole **projektu** na nazwę projektu.  
  
## <a name="defining-the-content-type"></a>Definiowanie typu zawartości  
  
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
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Łączenie rozszerzenia nazwy pliku z typem zawartości  
  
- Aby zmapować ten typ zawartości na rozszerzenie nazwy pliku, należy wyeksportować a <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> , który ma rozszerzenie ". HID" i typ zawartości "HID".  
  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Dodawanie typu zawartości do eksportu edytora  
  
1. Utwórz rozszerzenie edytora. Na przykład można użyć rozszerzenia symbolu marginesu opisanego w [przewodniku: Tworzenie glifu marginesu](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2. Dodaj klasę zdefiniowaną w tej procedurze.  
  
3. Podczas eksportowania klasy rozszerzeń należy dodać <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> do niej typ "HID".  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
