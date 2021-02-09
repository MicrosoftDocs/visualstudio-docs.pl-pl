---
title: Dodawanie kontrolek niestandardowych do okna źródeł danych
description: Dodaj niestandardowe kontrolki do okna źródła danych w programie Visual Studio. Dostosuj listę formantów możliwych do powiązania. Dodaj skojarzone kontrolki.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.openlocfilehash: 5591dc9c3422918fa8f9c605105ea10c8fbc447d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867428"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Dodawanie kontrolek niestandardowych do okna źródeł danych

Podczas przeciągania elementu z okna źródła danych do powierzchni projektowej w celu utworzenia formantu powiązanego z danymi można wybrać typ tworzonego formantu. Każdy element w oknie ma listę rozwijaną, która wyświetla kontrolki, spośród których można wybrać. Zestaw kontrolek skojarzonych z każdym elementem jest określany przez typ danych elementu. Jeśli formant, który chcesz utworzyć, nie znajduje się na liście, możesz wykonać instrukcje przedstawione w tym temacie, aby dodać formant do listy.

Aby uzyskać więcej informacji na temat wybierania formantów powiązanych z danymi do tworzenia dla elementów w oknie źródła danych, zobacz [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="customize-the-bindable-controls-list"></a>Dostosowywanie listy formantów możliwych do powiązania

Aby dodać lub usunąć kontrolki z listy dostępnych kontrolek dla elementów w oknie źródła danych, które mają określony typ danych, wykonaj następujące czynności.

### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Aby wybrać kontrolki, które mają być wyświetlane dla typu danych

1. Upewnij się, że Projektant WPF lub Projektant formularzy systemu Windows jest otwarty.

2. W oknie **źródła danych** kliknij element, który jest częścią źródła danych, które zostało dodane do okna, a następnie kliknij menu rozwijane dla elementu.

   > [!TIP]
   > Jeśli okno źródła danych nie jest otwarte, otwórz je, wybierając opcję **Wyświetl**  >  **inne**  >  **źródła danych** systemu Windows.

3. W menu rozwijanym kliknij opcję **Dostosuj**. Zostanie otwarte jedno z następujących okien dialogowych:

    - Jeśli **Projektant formularzy systemu Windows** jest otwarty, zostanie wyświetlona strona **Dostosowywanie interfejsu użytkownika danych** okna dialogowego **Opcje** . Aby uzyskać więcej informacji, zobacz [okno dialogowe Opcje dostosowywania interfejsu użytkownika danych](../ide/reference/options-windows-forms-designer-data-ui-customization.md).

    - Jeśli **Projektant WPF** jest otwarty, zostanie otwarte okno dialogowe **Dostosowywanie powiązania kontrolki** .

4. W oknie dialogowym Wybierz typ danych z listy rozwijanej **Typ danych** .

    - Aby dostosować listę formantów dla tabeli lub obiektu, wybierz pozycję **[Lista]**.

    - Aby dostosować listę kontrolek dla kolumny tabeli lub właściwości obiektu, wybierz typ danych kolumny lub właściwości w źródłowym magazynie danych.

    - Aby dostosować listę kontrolek do wyświetlania obiektów danych, które mają kształty zdefiniowane przez użytkownika, wybierz pozycję **[inne]**. Na przykład wybierz pozycję **[inne]** , jeśli aplikacja ma kontrolkę niestandardową, która wyświetla dane z więcej niż jednej właściwości określonego obiektu.

5. W polu **skojarzone kontrolki** zaznacz każdy formant, który ma być dostępny dla wybranego typu danych, lub usuń zaznaczenie wszystkich kontrolek, które chcesz usunąć z listy.

    > [!NOTE]
    > Jeśli kontrolka, która ma zostać wybrana, nie jest wyświetlana w polu **skojarzone kontrolki** , należy dodać formant do listy. Aby uzyskać więcej informacji, zobacz [Dodawanie skojarzonych kontrolek](#add-associated-controls).

6. Kliknij przycisk **OK**.

7. W oknie **źródła danych** kliknij element typu danych, do którego po prostu skojarzono jedną lub więcej kontrolek, a następnie kliknij menu rozwijane dla elementu.

     Kontrolki wybrane w polu **skojarzone kontrolki** są teraz wyświetlane w menu rozwijanym elementu.

## <a name="add-associated-controls"></a>Dodaj skojarzone kontrolki

Jeśli chcesz skojarzyć formant z typem danych, ale formant nie pojawia się w **skojarzonym polu formantów** , musisz dodać formant do listy. Formant musi znajdować się w bieżącym rozwiązaniu lub w przywoływanym zestawie. Musi również być dostępna w **przyborniku** i mieć atrybut, który określa zachowanie powiązania danych formantu.

Aby dodać kontrolki do listy skojarzonych formantów:

1. Dodaj żądany formant do **przybornika** , klikając go prawym przyciskiem **myszy i** wybierając **pozycję Wybierz elementy**.

     Kontrolka musi mieć jeden z następujących atrybutów:

    |Atrybut|Opis|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Zaimplementuj ten atrybut w prostych kontrolkach, które wyświetlają pojedynczą kolumnę (lub właściwość) danych, taką jak <xref:System.Windows.Forms.TextBox> .|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Zaimplementuj ten atrybut w kontrolkach, które wyświetlają listy (lub tabele) danych, takie jak <xref:System.Windows.Forms.DataGridView> .|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Zaimplementuj ten atrybut w kontrolkach, które wyświetlają listy (lub tabele) danych, ale muszą również przedstawić pojedynczą kolumnę lub właściwość, taką jak <xref:System.Windows.Forms.ComboBox> .|

2. Aby uzyskać Windows Forms, w oknie dialogowym **Opcje** Otwórz stronę **Dostosowywanie interfejsu użytkownika danych** . Lub w przypadku platformy WPF Otwórz okno dialogowe **Dostosowywanie powiązania kontrolki** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie listy formantów możliwych do powiązania dla typu danych](#customize-the-bindable-controls-list).

3. W polu **skojarzone formanty** , formant, który właśnie został dodany do **przybornika** , powinien teraz zostać wyświetlony.

    > [!NOTE]
    > Do listy skojarzonych formantów można dodawać tylko kontrolki znajdujące się w bieżącym rozwiązaniu lub w przywoływanym zestawie. (Kontrolki muszą także zaimplementować jeden z atrybutów powiązania danych w poprzedniej tabeli). Aby powiązać dane z kontrolką niestandardową, która nie jest dostępna w oknie źródła danych, przeciągnij kontrolkę z **przybornika** na powierzchnię projektu, a następnie przeciągnij element do elementu z okna **źródła danych** na kontrolkę.

## <a name="see-also"></a>Zobacz też

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Okno dialogowe Opcje dostosowywania interfejsu użytkownika danych](../ide/reference/options-windows-forms-designer-data-ui-customization.md)
