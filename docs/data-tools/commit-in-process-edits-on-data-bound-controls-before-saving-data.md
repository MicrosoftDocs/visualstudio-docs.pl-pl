---
title: Niezatwierdzone zmiany
description: Zatwierdź edycję w procesie dla kontrolek Windows Forms powiązanych z danymi przed zapisaniem danych. Wywołaj EndEdit dla wszystkich składników BindingSource w formularzu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 53101505230a51f109ace904c2f8322659733b4b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216322"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Zatwierdzanie edycji wewnątrzprocesowych w ramach kontrolek powiązanych z danymi przed zapisaniem danych

Podczas edytowania wartości w formantach powiązanych z danymi użytkownicy muszą wychodzący z bieżącego rekordu, aby zatwierdzić zaktualizowaną wartość do bazowego źródła danych, z którym jest powiązany formant. Gdy przeciągniesz elementy z [okna źródła danych](add-new-data-sources.md) na formularz, pierwszy element, który chcesz usunąć, generuje kod na przycisku **Zapisz** kliknij zdarzenie <xref:System.Windows.Forms.BindingNavigator> . Ten kod wywołuje <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodę <xref:System.Windows.Forms.BindingSource> . W związku z tym wywołanie <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody jest generowane tylko dla pierwszej <xref:System.Windows.Forms.BindingSource> , która jest dodawana do formularza.

<xref:System.Windows.Forms.BindingSource.EndEdit%2A>Wywołanie zatwierdza wszelkie zmiany, które są w toku, we wszystkich kontrolkach powiązanych z danymi, które są obecnie edytowane. W związku z tym, Jeśli kontrolka powiązane z danymi nadal ma fokus i klikniesz przycisk **Zapisz** , wszystkie oczekujące zmiany w tym formancie zostaną zatwierdzone przed rzeczywistym zapisem ( `TableAdapterManager.UpdateAll` Metoda).

Można skonfigurować aplikację do automatycznego zatwierdzania zmian, nawet jeśli użytkownik próbuje zapisać dane bez zatwierdzania zmian w ramach procesu zapisywania.

> [!NOTE]
> Projektant dodaje `BindingSource.EndEdit` kod tylko dla pierwszego elementu upuszczanego na formularz. W związku z tym należy dodać wiersz kodu, aby wywołać <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodę dla każdej z nich <xref:System.Windows.Forms.BindingSource> w formularzu. Możesz ręcznie dodać wiersz kodu, aby wywołać <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodę dla każdej z nich <xref:System.Windows.Forms.BindingSource> . Alternatywnie możesz dodać `EndEditOnAllBindingSources` metodę do formularza i wywołać ją przed wykonaniem zapisywania.

Poniższy kod używa zapytania [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) do iterowania wszystkich <xref:System.Windows.Forms.BindingSource> składników i wywołania <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody dla każdego <xref:System.Windows.Forms.BindingSource> w formularzu.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Aby wywołać EndEdit dla wszystkich składników BindingSource w formularzu

1. Dodaj następujący kod do formularza zawierającego <xref:System.Windows.Forms.BindingSource> składniki.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet1":::

2. Dodaj następujący wiersz kodu bezpośrednio przed dowolnymi wywołaniami, aby zapisać dane formularza ( `TableAdapterManager.UpdateAll()` Metoda):

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb" id="Snippet2":::

## <a name="see-also"></a>Zobacz też

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)
