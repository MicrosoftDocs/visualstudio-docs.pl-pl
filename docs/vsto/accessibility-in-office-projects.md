---
title: Ułatwienia dostępu w projektach pakietu Office
description: Dowiedz się, w jaki sposób projekty Microsoft Office zawierają wiele funkcji ułatwień dostępu, które umożliwiają tworzenie niestandardowych rozwiązań spełniających standardowe wymagania dotyczące ułatwień dostępu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: de877ccc2d2a036bf03b0888a7edf455b17788a4
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847367"
---
# <a name="accessibility-in-office-projects"></a>Ułatwienia dostępu w projektach pakietu Office

Microsoft Visual Studio i Microsoft Office obejmują wiele funkcji ułatwień dostępu, które umożliwiają tworzenie niestandardowych rozwiązań spełniających standardowe wymagania dotyczące ułatwień dostępu. Firma Microsoft publikuje wytyczne dotyczące ułatwień dostępu w sieci Web. Aby uzyskać szczegółowe informacje, zobacz [witrynę sieci Web ułatwień dostępu](https://www.microsoft.com/accessibility/).

W większości przypadków projekty pakietu Office w programie Visual Studio spełniają standardy dostępności lub udostępniają właściwości, które można ustawić w celu udostępnienia rozwiązań. Istnieją jednak pewne funkcje z ograniczoną dostępnością.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Ułatwienia dostępu w czasie projektowania

### <a name="use-shortcut-keys-in-document-level-projects"></a>Używanie klawiszy skrótów w projektach na poziomie dokumentu
 Gdy Microsoft Office dokument programu Word Microsoft Office lub skoroszyt programu Excel jest otwarty w programie Visual Studio, tylko jedna aplikacja w danym momencie otrzymuje polecenia klawiszy skrótu. Domyślnie program Visual Studio otrzymuje wszystkie polecenia klawisza skrótu, ale w programie Word lub Excel można je odebrać, gdy dokument ma fokus, wybierając **dynamiczny schemat klawiatury** na stronie **Ustawienia klawiatury** okna dialogowego **Opcje** . Aby uzyskać więcej informacji, zobacz [Microsoft Office klawiatury, Microsoft Office ustawienia klawiatury, okno dialogowe Opcje](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) i [Microsoft Office klawiatura programu Excel, Microsoft Office ustawienia klawiatury, okno dialogowe Opcje](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Wyświetlaj klawisze skrótów dla wstążki w projektach na poziomie dokumentu
 Gdy dokument programu Word lub skoroszyt programu Excel jest otwarty w programie Visual Studio, nie można nacisnąć klawisza **Alt** , aby wyświetlić klawisze skrótów dla kart i kontrolek na Wstążce. Aby wyświetlić skróty klawiaturowe, gdy dokument lub skoroszyt jest otwarty w projektancie, wykonaj następujące czynności.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Aby wyświetlić klawisze skrótów dla kart wstążki i kontrolek w projektancie

1. W programie Visual Studio w menu **Narzędzia** kliknij pozycję **Opcje**.

2. Rozwiń węzeł **Narzędzia pakietu Office** , a następnie wybierz Microsoft Office opcję klawiatura **programu Excel** lub **program Microsoft Office Word**, zgodnie z potrzebami.

3. Wybierz **dynamiczny schemat klawiatury**.

     Zostanie wyświetlony komunikat z informacją, że musisz ponownie uruchomić program Visual Studio, aby zmiany zaczęły obowiązywać.

4. Kliknij przycisk **OK**.

5. Uruchom ponownie program Visual Studio i Otwórz projekt.

6. Otwórz projektanta dokumentu lub skoroszytu dla projektu.

7. Naciśnij klawisz **F6** , aby wyświetlić klawisze skrótów dla wstążki.

## <a name="accessibility-at-run-time"></a>Ułatwienia dostępu w czasie wykonywania

### <a name="windows-forms-controls-on-office-documents"></a>Kontrolki Windows Forms w dokumentach pakietu Office
 Formanty Windows Forms uwidaczniają właściwości ułatwień dostępu, aby zapewnić informacje o kontroli dostępu do pomocy, takich jak czytniki ekranu. Możesz skorzystać z tych właściwości ułatwień dostępu, gdy formanty znajdują się w dokumencie pakietu Office w dostosowaniu na poziomie dokumentu. Aby uzyskać więcej informacji, zobacz temat [zapewnianie informacji o ułatwieniach dostępu dla kontrolek w formularzu systemu Windows](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 Istnieją jednak pewne ograniczenia dotyczące ułatwień dostępu w czasie wykonywania, gdy formanty Windows Forms są hostowane w skoroszycie programu Excel lub w dokumencie programu Word:

- Nie można przetab z jednej kontrolki do innej.

- Kontrolki dokumentu są wyłączone w przypadku zmiany ustawienia powiększenia dokumentu na inne niż 100%.

  Aby uzyskać informacje na temat ograniczeń Windows Forms formantów w dokumentach, zobacz [ograniczenia Windows Forms formantów w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Okienka akcji i niestandardowe okienka zadań
 Gdy okienko akcji lub niestandardowe okienko zadań ma fokus, można uzyskać dostęp do kontrolek w taki sam sposób, w jaki uzyskuje się dostęp do kontrolek w aplikacji Windows Forms. Aby przenieść kursor między okienkiem akcje a dokumentem, możesz nacisnąć klawisz **F6**.

 Aby uzyskać więcej informacji na temat okienek akcji i niestandardowych okienek zadań, zobacz [Omówienie okienka Akcje](../vsto/actions-pane-overview.md) i [niestandardowe okienka zadań](../vsto/custom-task-panes.md).

### <a name="display-modes"></a>Tryby wyświetlania

Program Visual Studio ma następujące ograniczenia związane z trybami wyświetlania:

- Kontrolki w dokumencie programu Word lub arkuszu programu Excel są wyłączone po zmianie ustawienia powiększenia dokumentu na inne niż 100%.

- W oknie dialogowym **Nowy projekt** nie są wyświetlane kontrolki prawidłowo, jeśli użytkownik zmieni opcje ułatwień dostępu na komputerze, aby **użyć duży kontrast**.

Aby obejść te ograniczenia, można użyć lupy. Lupa to narzędzie do wyświetlania w systemie Windows, które tworzy osobne okno, które wyświetla powiększoną część ekranu.

## <a name="see-also"></a>Zobacz także

- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Ułatwienia dostępu dla osób niepełnosprawnych](../ide/reference/accessibility-features-of-visual-studio.md)
- [Funkcje ułatwień dostępu programu Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)