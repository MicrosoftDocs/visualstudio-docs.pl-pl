---
title: 'Przewodnik: Łączenie typu zawartości z rozszerzeniem nazwy pliku | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076618"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Przewodnik: Łączenie typu zawartości z rozszerzeniem nazwy pliku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zdefiniować typu zawartości i połączyć rozszerzenie nazwy pliku przy użyciu rozszerzenia Managed Extensibility Framework (MEF) edytora. W niektórych przypadkach rozszerzenie nazwy pliku został już zdefiniowany przez usługę języka; Niemniej jednak pomocą MEF nadal należy połączyć je typu zawartości.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
1. Utwórz projekt VSIX języka C#. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projekt VSIX**.) Nazwij rozwiązanie `ContentTypeTest`.  
  
2. W **source.extension.vsixmanifest** pliku, przejdź do **zasoby** , a następnie ustaw **typu** pole **Microsoft.VisualStudio.MefComponent**, **źródła** pole **projekt w bieżącym rozwiązaniu**i **projektu** pola Nazwa projektu.  
  
## <a name="defining-the-content-type"></a>Definiowanie typu zawartości  
  
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
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Rozszerzenie nazwy pliku — łączenie typu zawartości  
  
- Aby zamapować tego typu zawartości na rozszerzenie nazwy pliku, należy wyeksportować <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> który ma rozszerzenie "HID" i typ zawartości "hid".  
  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Dodawanie typu zawartości do edytora eksportowanie  
  
1. Tworzenie rozszerzenia edytora. Na przykład, można użyć rozszerzenia symbol margines opisanego w [instruktażu: Tworzenie marginesie](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2. Dodaj klasę, które zostały zdefiniowane w tej procedurze.  
  
3. Podczas eksportowania klasy rozszerzenia, Dodaj <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> typu "hid" do niego.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
