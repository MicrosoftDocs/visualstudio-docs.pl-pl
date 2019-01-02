---
title: 'Instrukcje: Programowe tworzenie nowych dokumentów programu Visio'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0962c0d7927fd7b21969b36020e2a40d587cf452
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872508"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Instrukcje: Programowe tworzenie nowych dokumentów programu Visio
  Podczas tworzenia nowego rysunku programu Microsoft Office Visio dokumentu, należy dodać go do `Microsoft.Office.Interop.Visio.Documents` zbiór otwarte dokumenty programu Visio. W związku z tym `Microsoft.Office.Interop.Visio.Documents.Add` metoda tworzy nowy dokument rysunku programu Visio. Aby uzyskać więcej informacji, zobacz dokumentację referencyjną VBA [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) metody.  
  
## <a name="create-new-blank-documents"></a>Tworzenie nowych dokumentów puste  
  
### <a name="to-create-a-new-document"></a>Aby utworzyć nowy dokument  
  
-   Użyj `Microsoft.Office.Interop.Visio.Documents.Add` metodę, aby utworzyć nowy pusty dokument, który nie jest oparty na szablonie.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="create-documents-copied-from-existing-documents"></a>Tworzenie dokumentów, skopiowane z istniejących dokumentów  
 `Microsoft.Office.Interop.Visio.Documents.Add` Metody można utworzyć nowy dokument, który jest kopią istniejącego dokumentu programu Visio. Musisz podać nazwę pliku i w pełni kwalifikowaną ścieżkę diagramu.  
  
### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Aby utworzyć nowy dokument, który jest kopiowany z istniejącego dokumentu  
  
-   Wywołaj `Microsoft.Office.Interop.Visio.Documents.Add` metody i określ ścieżkę na diagramie programu Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="create-stencils-copied-from-existing-stencils"></a>Utwórz wzorników skopiowane z istniejącego wzorników  
 [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) metody można utworzyć nowego wzornik kopię istniejącego wzornika programu Visio. Musisz podać nazwę pliku i w pełni kwalifikowana ścieżka wzornika.  
  
### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Aby utworzyć nowy wzornik skopiowane z istniejącego wzornika  
  
-   Wywołaj `Microsoft.Office.Interop.Visio.Documents.Add` metody i określ ścieżkę wzornika.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="create-documents-based-on-existing-templates"></a>Tworzenie dokumentów na podstawie istniejących szablonów  
 `Microsoft.Office.Interop.Visio.Documents.Add` Metody można utworzyć nowy dokument ( *VSD* pliku) opartego na podstawie istniejącego szablonu programu Visio ( *.vst* pliku). Ta metoda powoduje skopiowanie wzorników, style i ustawienia, które są częścią obszaru roboczego szablonu. Musisz podać nazwę pliku i w pełni kwalifikowana ścieżka szablonu.  
  
### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Aby utworzyć nowy dokument, który jest oparty na podstawie istniejącego szablonu  
  
-   Wywołaj `Microsoft.Office.Interop.Visio.Documents.Add` metody i określ ścieżkę do szablonu.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Ten przykład kodu wymaga następujących elementów:  
  
-   Dokument programu Visio o nazwie `myDrawing.vsd` musi znajdować się w katalogu o nazwie `Test` w *Moje dokumenty* folder (Windows XP i starszych) lub *dokumenty* folder (Windows Vista).  
  
-   Dokument programu Visio o nazwie `myStencil.vss` musi znajdować się w katalogu o nazwie `Test` w *Moje dokumenty* folder (Windows XP i starszych) lub *dokumenty* folder (Windows Vista).  
  
-   Dokument programu Visio o nazwie `myTemplate.vst` musi znajdować się w katalogu o nazwie `Test` w *Moje dokumenty* folder (Windows XP i starszych) lub *dokumenty* folder (Windows Vista).  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwiązania programu Visio](../vsto/visio-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Instrukcje: Programowe otwieranie dokumentów programu Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Instrukcje: Programowe zamykanie dokumentów programu Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Instrukcje: Programowe zapisywanie dokumentów programu Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Instrukcje: Programowe drukowanie dokumentów programu Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
