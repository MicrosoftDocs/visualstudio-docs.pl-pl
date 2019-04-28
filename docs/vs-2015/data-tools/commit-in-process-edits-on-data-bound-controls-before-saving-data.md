---
title: Zatwierdź zmiany w procesie kontrolek powiązanych z danymi przed zapisaniem danych | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 03fab773ed6842bc21552d060797b331d9f73770
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437037"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Zatwierdzanie edycji wewnątrzprocesowych w ramach kontrolek powiązanych z danymi przed zapisaniem danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas edytowania wartości w formantach powiązanych z danymi, użytkownicy muszą Wyjdź bieżącego rekordu, aby zatwierdzić zaktualizowaną wartość do bazowego źródła danych, który formant jest powiązany z. Podczas przeciągania elementów z [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) na formularz, pierwszy element, który usuniesz generuje kod z gałęzią **Zapisz** Zdarzenie kliknięcia przycisku <xref:System.Windows.Forms.BindingNavigator>. Ten kod wywołuje <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody <xref:System.Windows.Forms.BindingSource>. W związku z tym, wywołanie <xref:System.Windows.Forms.BindingSource.EndEdit%2A> ma generowaną metodę tylko pierwszy <xref:System.Windows.Forms.BindingSource> który został dodany do formularza.  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Wywołanie zatwierdza wszystkie zmiany, które jest obecnie w toku w żadnych formantów powiązanych z danymi, które są aktualnie edytowanym. W związku z tym, jeśli formant powiązany z danymi nadal ma fokus i kliknij przycisk **Zapisz** przycisk wszystkie oczekujące zmiany, w tym, że kontrolki są zatwierdzane przed rzeczywiste Zapisz ( `TableAdapterManager.UpdateAll` metody).  
  
 Można skonfigurować aplikację do automatycznego zatwierdzania zmian, nawet wtedy, gdy użytkownik próbuje zapisać dane bez zatwierdzania zmian, Zapisz w ramach procesu.  
  
> [!NOTE]
> Projektant dodaje `BindingSource.EndEdit` kod tylko dla pierwszego elementu upuszczone na formularzu. W związku z tym, należy dodać wiersz kodu w celu wywołania <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody dla każdego <xref:System.Windows.Forms.BindingSource> w formularzu. Można ręcznie dodać wiersz kodu w celu wywołania <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody dla każdego <xref:System.Windows.Forms.BindingSource>. Alternatywnie, można dodać `EndEditOnAllBindingSources` metody do formularza, a następnie wywołaj ją przed wykonaniem zapisywania.  
  
 Poniższy kod używa [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) zapytania do wszystkich iteracji <xref:System.Windows.Forms.BindingSource> składników i wywołania <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody dla każdego <xref:System.Windows.Forms.BindingSource> w formularzu.  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Aby wywołać EndEdit — dla wszystkich składników BindingSource w formularzu  
  
1. Dodaj następujący kod do formularza, który zawiera <xref:System.Windows.Forms.BindingSource> składników.  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]  
  
2. Dodaj następujący wiersz kodu, tuż przed wszelkie wywołania, aby zapisać dane formularza ( `TableAdapterManager.UpdateAll()` metoda):  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązywanie kontrolek formularzy Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)
