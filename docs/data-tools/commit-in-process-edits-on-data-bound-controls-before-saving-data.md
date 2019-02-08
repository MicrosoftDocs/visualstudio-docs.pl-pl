---
title: Zatwierdzanie edycji wewnątrzprocesowych w ramach kontrolek powiązanych z danymi przed zapisaniem danych
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4f57b21117f5fd5a4ff7c0403afe9cdbd63ec342
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55950451"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Zatwierdzanie edycji wewnątrzprocesowych w ramach kontrolek powiązanych z danymi przed zapisaniem danych

Podczas edytowania wartości w formantach powiązanych z danymi, użytkownicy muszą Wyjdź bieżącego rekordu, aby zatwierdzić zaktualizowaną wartość do bazowego źródła danych, który formant jest powiązany z. Podczas przeciągania elementów z [okna źródeł danych](add-new-data-sources.md) na formularz, pierwszy element, który usuniesz generuje kod z gałęzią **Zapisz** Zdarzenie kliknięcia przycisku <xref:System.Windows.Forms.BindingNavigator>. Ten kod wywołuje <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody <xref:System.Windows.Forms.BindingSource>. W związku z tym, wywołanie <xref:System.Windows.Forms.BindingSource.EndEdit%2A> ma generowaną metodę tylko pierwszy <xref:System.Windows.Forms.BindingSource> który został dodany do formularza.

<xref:System.Windows.Forms.BindingSource.EndEdit%2A> Wywołanie zatwierdza wszystkie zmiany, które jest obecnie w toku w żadnych formantów powiązanych z danymi, które są aktualnie edytowanym. W związku z tym, jeśli formant powiązany z danymi nadal ma fokus i kliknij przycisk **Zapisz** przycisk wszystkie oczekujące zmiany, w tym, że kontrolki są zatwierdzane przed rzeczywiste Zapisz ( `TableAdapterManager.UpdateAll` metody).

Można skonfigurować aplikację do automatycznego zatwierdzania zmian, nawet wtedy, gdy użytkownik próbuje zapisać dane bez zatwierdzania zmian, Zapisz w ramach procesu.

> [!NOTE]
> Projektant dodaje `BindingSource.EndEdit` kod tylko dla pierwszego elementu upuszczone na formularzu. W związku z tym, należy dodać wiersz kodu w celu wywołania <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody dla każdego <xref:System.Windows.Forms.BindingSource> w formularzu. Można ręcznie dodać wiersz kodu w celu wywołania <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody dla każdego <xref:System.Windows.Forms.BindingSource>. Alternatywnie, można dodać `EndEditOnAllBindingSources` metody do formularza, a następnie wywołaj ją przed wykonaniem zapisywania.

Poniższy kod używa [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) zapytania do wszystkich iteracji <xref:System.Windows.Forms.BindingSource> składników i wywołania <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody dla każdego <xref:System.Windows.Forms.BindingSource> w formularzu.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Aby wywołać EndEdit — dla wszystkich składników BindingSource w formularzu

1.  Dodaj następujący kod do formularza, który zawiera <xref:System.Windows.Forms.BindingSource> składników.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2.  Dodaj następujący wiersz kodu, tuż przed wszelkie wywołania, aby zapisać dane formularza ( `TableAdapterManager.UpdateAll()` metoda):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)