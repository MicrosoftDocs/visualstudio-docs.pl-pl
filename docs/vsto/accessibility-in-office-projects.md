---
title: Ułatwienia dostępu w projektach pakietu Office
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 32d44c33192d9d4e4fdcf1b8db8cb47102a1df61
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833329"
---
# <a name="accessibility-in-office-projects"></a>Ułatwienia dostępu w projektach pakietu Office

Microsoft Visual Studio i Microsoft Office zawiera wiele funkcji ułatwień dostępu, które umożliwiają tworzenie niestandardowych rozwiązań, które spełniają wymagania standardowych ułatwień dostępu. Firma Microsoft publikuje wytyczne dotyczące ułatwień dostępu w sieci Web. Aby uzyskać więcej informacji, zobacz [WWW ułatwień dostępu](http://go.microsoft.com/fwlink/?LinkID=37113).

W większości przypadków projektów pakietu Office w Visual Studio spełnia ułatwień dostępu standardów lub udostępnia właściwości, które można ustawić, aby udostępnić swoje rozwiązania. Istnieją jednak pewne funkcje, które mają ograniczoną dostępność.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Ułatwienia dostępu w czasie projektowania

### <a name="use-shortcut-keys-in-document-level-projects"></a>Klawisze skrótów w projektach na poziomie dokumentu
 Gdy dokument programu Microsoft Office Word lub skoroszytu programu Microsoft Office Excel jest otwarty w programie Visual Studio, tylko jedną aplikację naraz otrzymuje polecenia klawiszy skrótów. Domyślnie program Visual Studio odbiera wszystkie polecenia klawiszy skrótów, ale możesz wprowadzać programu Word lub Excel ich otrzymywania, gdy dokument ma fokus, wybierając **dynamiczny schemat klawiatury** na **ustawienia klawiatury** strony z **opcje** okno dialogowe. Aby uzyskać więcej informacji, zobacz [klawiatura programu Microsoft Office Word, ustawienia klawiatury Microsoft Office, okno dialogowe Opcje](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) i [klawiatura programu Microsoft Office Excel, ustawienia klawiatury Microsoft Office, okno dialogowe Opcje](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Wyświetla klawiszy skrótów dla wstążki w projektach na poziomie dokumentu
 Gdy dokument programu Word lub skoroszytu programu Excel jest otwarty w programie Visual Studio, nie można nacisnąć klawisza **Alt** klawisz, aby wyświetlić klawisze skrótów dla kart i kontrolek na Wstążce. Aby wyświetlić klawisze skrótów, gdy dokument lub skoroszyt jest otwarty w projektancie, wykonaj następujące czynności.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Aby wyświetlić klawisze skrótów dla karty Wstążki i formantów w Projektancie

1.  W programie Visual Studio na **narzędzia** menu, kliknij przycisk **opcje**.

2.  Rozwiń **narzędzia Office** , a następnie wybierz węzeł **klawiatura programu Microsoft Office Excel** lub **klawiatura programu Microsoft Office Word**, odpowiednio.

3.  Wybierz **dynamiczny schemat klawiatury**.

     Pojawi się komunikat z informacją, że należy ponownie uruchomić Visual Studio aby zmiany zaczęły obowiązywać.

4.  Kliknij przycisk **OK**.

5.  Uruchom ponownie program Visual Studio i otwórz ponownie projekt.

6.  Otwórz dokument lub skoroszyt, Projektant projektu.

7.  Naciśnij klawisz **F6** spowoduje wyświetlanie klawiszy skrótów dla wstążki.

## <a name="accessibility-at-runtime"></a>Ułatwienia dostępu w czasie wykonywania

### <a name="windows-forms-controls-on-office-documents"></a>Formanty Windows Forms w dokumentach pakietu Office
 Formanty Windows Forms zmieniają właściwości ułatwień dostępu w celu dostarczenia informacji o kontroli do narzędzi ułatwień dostępu, takich jak czytniki zawartości ekranu. Możesz korzystać z zalet tych właściwości ułatwień dostępu w przypadku kontrolek w dokumencie programu Word w dostosowaniu na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz [Podaj informacje o ułatwieniach dostępu dla formantów w formularzu Windows](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 Istnieją pewne ograniczenia ułatwień dostępu w czasie wykonywania w przypadku kontrolek formularzy Windows Forms znajdują się w skoroszycie programu Excel lub dokumentu programu Word:

- Nie można kartę z jednego formantu do drugiego.

- Kontrolki do dokumentu są wyłączone, gdy ustawienie powiększenia dokumentu zostanie zmieniony na coś innego niż 100%.

  Aby uzyskać informacje o ograniczeniach formanty Windows Forms w dokumentach, zobacz [ograniczenia Windows Forms kontrolki w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Okienka akcji i niestandardowych okienek zadań
 Gdy okienko akcji lub niestandardowego okienka zadań ma fokus, możesz uzyskać dostęp formantów taki sam sposób, dostęp do formantów w aplikacji Windows Forms. Aby przenieść kursor między panelu actions i dokumentu, możesz nacisnąć przycisk **F6**.

 Aby uzyskać więcej informacji na temat okienka akcji i niestandardowych okienek zadań, zobacz [okienko akcji ― omówienie](../vsto/actions-pane-overview.md) i [niestandardowych okienek zadań](../vsto/custom-task-panes.md).

### <a name="display-modes"></a>Tryby wyświetlania

Program Visual Studio ma następujące ograniczenia związane z tryby wyświetlania:

- Formanty w dokumencie programu Word lub arkusz programu Excel są wyłączone, gdy ustawienie powiększenia dokumentu zostanie zmieniony na coś innego niż 100%.

- **Nowy projekt** okno dialogowe nie są wyświetlane formantów poprawnie, jeśli użytkownik zmieni opcji ułatwień dostępu komputera do **użycie o wysokim kontraście**.

Program Lupa można użyć, aby wyeliminować te ograniczenia. Lupa jest narzędzie do wyświetlania w Windows, która tworzy osobne okno, które wyświetla powiększony część ekranu.

## <a name="see-also"></a>Zobacz także

- [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Ułatwienia dostępu dla osób niepełnosprawnych](../ide/reference/accessibility-for-people-with-disabilities.md)
- [Funkcje ułatwień dostępu programu Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)