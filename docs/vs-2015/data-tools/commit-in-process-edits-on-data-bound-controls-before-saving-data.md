---
title: Zatwierdź edycję w procesie w formantach powiązanych z danymi przed zapisaniem danych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3867b91a8b417b5670514b66aaf93fdab4e9618c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662454"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Zatwierdzanie edycji wewnątrzprocesowych w ramach kontrolek powiązanych z danymi przed zapisaniem danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas edytowania wartości w formantach powiązanych z danymi użytkownicy muszą wychodzący z bieżącego rekordu, aby zatwierdzić zaktualizowaną wartość do bazowego źródła danych, z którym jest powiązany formant. Gdy przeciągniesz elementy z [okna źródła danych](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) na formularz, pierwszy element, który chcesz usunąć, generuje kod na przycisku **zapisz** kliknij zdarzenie <xref:System.Windows.Forms.BindingNavigator>. Ten kod wywołuje metodę <xref:System.Windows.Forms.BindingSource.EndEdit%2A> <xref:System.Windows.Forms.BindingSource>. W związku z tym wywołanie metody <xref:System.Windows.Forms.BindingSource.EndEdit%2A> jest generowane tylko dla pierwszej <xref:System.Windows.Forms.BindingSource>, która jest dodawana do formularza.

 Wywołanie <xref:System.Windows.Forms.BindingSource.EndEdit%2A> zatwierdza wszelkie zmiany, które są w toku, w dowolnych kontrolkach powiązanych z danymi, które są obecnie edytowane. W związku z tym, Jeśli kontrolka powiązane z danymi nadal ma fokus, a klikniesz przycisk **Zapisz** , wszystkie oczekujące zmiany w tym formancie są zatwierdzane przed rzeczywistym zapisem (`TableAdapterManager.UpdateAll` metodzie).

 Można skonfigurować aplikację do automatycznego zatwierdzania zmian, nawet jeśli użytkownik próbuje zapisać dane bez zatwierdzania zmian w ramach procesu zapisywania.

> [!NOTE]
> Projektant dodaje kod `BindingSource.EndEdit` tylko dla pierwszego elementu upuszczanego na formularz. W związku z tym należy dodać wiersz kodu, aby wywołać metodę <xref:System.Windows.Forms.BindingSource.EndEdit%2A> dla każdej <xref:System.Windows.Forms.BindingSource> w formularzu. Możesz ręcznie dodać wiersz kodu, aby wywołać metodę <xref:System.Windows.Forms.BindingSource.EndEdit%2A> dla każdej <xref:System.Windows.Forms.BindingSource>. Alternatywnie możesz dodać metodę `EndEditOnAllBindingSources` do formularza i wywołać ją przed wykonaniem zapisywania.

 Poniższy kod używa zapytania [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) do iteracji wszystkich składników <xref:System.Windows.Forms.BindingSource> i wywoływać metodę <xref:System.Windows.Forms.BindingSource.EndEdit%2A> dla każdego <xref:System.Windows.Forms.BindingSource> w formularzu.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Aby wywołać EndEdit dla wszystkich składników BindingSource w formularzu

1. Dodaj następujący kod do formularza zawierającego składniki <xref:System.Windows.Forms.BindingSource>.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]

2. Dodaj następujący wiersz kodu bezpośrednio przed dowolnymi wywołaniami, aby zapisać dane formularza (Metoda `TableAdapterManager.UpdateAll()`):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]

## <a name="see-also"></a>Zobacz też
 [Powiązywanie formantów Windows Forms z danymi w](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [hierarchicznej aktualizacji](../data-tools/hierarchical-update.md) programu Visual Studio
