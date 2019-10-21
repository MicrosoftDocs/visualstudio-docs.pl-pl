---
title: Zatwierdź edycję w procesie w formantach powiązanych z danymi przed zapisaniem
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 129f8e03ca982dc1e028dc23a9e342b5793e39cf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648674"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Zatwierdzanie edycji wewnątrzprocesowych w ramach kontrolek powiązanych z danymi przed zapisaniem danych

Podczas edytowania wartości w formantach powiązanych z danymi użytkownicy muszą wychodzący z bieżącego rekordu, aby zatwierdzić zaktualizowaną wartość do bazowego źródła danych, z którym jest powiązany formant. Gdy przeciągniesz elementy z [okna źródła danych](add-new-data-sources.md) na formularz, pierwszy element, który chcesz usunąć, generuje kod na przycisku **zapisz** kliknij zdarzenie <xref:System.Windows.Forms.BindingNavigator>. Ten kod wywołuje metodę <xref:System.Windows.Forms.BindingSource.EndEdit%2A> <xref:System.Windows.Forms.BindingSource>. W związku z tym wywołanie metody <xref:System.Windows.Forms.BindingSource.EndEdit%2A> jest generowane tylko dla pierwszej <xref:System.Windows.Forms.BindingSource>, która jest dodawana do formularza.

Wywołanie <xref:System.Windows.Forms.BindingSource.EndEdit%2A> zatwierdza wszelkie zmiany, które są w toku, w dowolnych kontrolkach powiązanych z danymi, które są obecnie edytowane. W związku z tym, Jeśli kontrolka powiązane z danymi nadal ma fokus, a klikniesz przycisk **Zapisz** , wszystkie oczekujące zmiany w tym formancie są zatwierdzane przed rzeczywistym zapisem (`TableAdapterManager.UpdateAll` metodzie).

Można skonfigurować aplikację do automatycznego zatwierdzania zmian, nawet jeśli użytkownik próbuje zapisać dane bez zatwierdzania zmian w ramach procesu zapisywania.

> [!NOTE]
> Projektant dodaje kod `BindingSource.EndEdit` tylko dla pierwszego elementu upuszczanego na formularz. W związku z tym należy dodać wiersz kodu, aby wywołać metodę <xref:System.Windows.Forms.BindingSource.EndEdit%2A> dla każdej <xref:System.Windows.Forms.BindingSource> w formularzu. Możesz ręcznie dodać wiersz kodu, aby wywołać metodę <xref:System.Windows.Forms.BindingSource.EndEdit%2A> dla każdej <xref:System.Windows.Forms.BindingSource>. Alternatywnie możesz dodać metodę `EndEditOnAllBindingSources` do formularza i wywołać ją przed wykonaniem zapisywania.

Poniższy kod używa zapytania [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) do iteracji wszystkich składników <xref:System.Windows.Forms.BindingSource> i wywoływać metodę <xref:System.Windows.Forms.BindingSource.EndEdit%2A> dla każdego <xref:System.Windows.Forms.BindingSource> w formularzu.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Aby wywołać EndEdit dla wszystkich składników BindingSource w formularzu

1. Dodaj następujący kod do formularza zawierającego składniki <xref:System.Windows.Forms.BindingSource>.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2. Dodaj następujący wiersz kodu bezpośrednio przed dowolnymi wywołaniami, aby zapisać dane formularza (Metoda `TableAdapterManager.UpdateAll()`):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)