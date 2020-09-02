---
title: 'Instrukcje: Ustawianie opcji ułatwień dostępu IDE | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: afff9e06c4333f4910e22e963d24090c1d1e4c6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651333"
---
# <a name="how-to-set-ide-accessibility-options"></a>Porady: ustawianie opcji ułatwień dostępu IDE
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zawiera funkcje, które ułatwiają osobom, które mają słabą wizję do odczytu i dla osób, które mają ograniczoną ruch. Te funkcje obejmują zmianę rozmiaru i koloru tekstu w edytorach, zmianę rozmiaru tekstu i przycisków na paskach narzędzi oraz Autouzupełnianie dla metod i parametrów, aby podać kilka nazw.

 Dodatkowo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsługuje układy klawiatury Dvoraka, które sprawiają, że najczęściej wpisywane znaki są bardziej dostępne. Można również dostosować domyślne klawisze skrótów dostępne w programie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Aby uzyskać więcej informacji, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="editors-dialogs-and-tool-windows"></a>Edytory, okna dialogowe i okna narzędzi
 Domyślnie okna dialogowe i okna narzędzi w programie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] używają tego samego rozmiaru i koloru czcionki co system operacyjny. Ustawienia koloru dla ramki środowiska IDE, okien dialogowych, pasków narzędzi i okien narzędzi są oparte na schemacie kolorów: jasne lub ciemne. Bieżący motyw kolorów można zmienić w [oknie dialogowym ogólne, środowisko, opcje](../../ide/reference/general-environment-options-dialog-box.md).

 Okna podręczne można także wyświetlić w widoku Kod edytora. Te okna mogą monitować o dostępne elementy członkowskie bieżącego obiektu i parametry, aby ukończyć funkcję lub instrukcję. Te okna mogą być przydatne, jeśli masz problemy z wpisywaniem. Jednak zakłócają one fokus w edytorze kodu, co może być problematyczne dla niektórych użytkowników. Możesz wyłączyć te okna, otwierając okno dialogowe Opcje i czyszcząc **listę członków** i **Informacje o parametrach** w **edytorze tekstu**, **wszystkie języki**, **Ogólne** strony w oknie dialogowym **Opcje** . Aby uzyskać więcej informacji, zobacz [How to: Set General Editor Options](https://msdn.microsoft.com/704e4a7b-2162-4bed-8a47-f4f6ffec98c2).

 Możesz zmienić rozmieszczenie systemu Windows w zintegrowanym środowisku programistycznym (IDE), aby najlepiej dopasować się do pracy. Każde okno narzędzi można zadokować, przepływać, ukryć lub automatycznie ukryć.

 Aby uzyskać więcej informacji na temat zmiany układów okien, zobacz [Dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="changing-the-size-of-text"></a>Zmiana rozmiaru tekstu
 Można zmienić ustawienia okien narzędzi tekstowych, takich jak okno **polecenia** , okno **bezpośrednie** i okno **dane wyjściowe** , w okienku **czcionki i kolory** w opcjach **środowiska** w oknie dialogowym **Narzędzia** . Po wybraniu opcji **[wszystkie okna narzędzi tekstowych]** na liście rozwijanej **Pokaż ustawienia dla** , ustawienie domyślne zostanie wyświetlone na liście rozwijanej na **pierwszym planie elementu** **i w** **tle elementu** . Możesz również zmienić ustawienia wyświetlania tekstu w edytorze.

##### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Aby zmienić rozmiar tekstu w oknach narzędzi tekstowych i edytorach

1. W menu **Narzędzia** wybierz polecenie **Opcje**.

2. Wybierz **czcionki i kolory** w folderze **Environment** .

3. Wybierz opcję z menu rozwijanego **Pokaż ustawienia dla** .

     Aby zmienić rozmiar czcionki dla tekstu w edytorze, wybierz **Edytor tekstu**.

     Aby zmienić rozmiar czcionki dla tekstu w oknach narzędzi tekstowych, wybierz opcję **[wszystkie okna narzędzi tekstowych]**.

     Aby zmienić rozmiar czcionki dla tekstu etykietki narzędzia w edytorze, wybierz **etykietkę narzędzia edytora**.

     Aby zmienić rozmiar czcionki dla tekstu w okienkach wyskakujących uzupełniania instrukcji, wybierz opcję **uzupełnianie instrukcji**.

4. Z **elementów wyświetlanych**wybierz opcję **zwykły tekst**.

5. W polu **czcionka**wybierz nowy typ czcionki.

6. W polu **rozmiar**wybierz nowy rozmiar czcionki.

    > [!NOTE]
    > Aby zresetować rozmiar tekstu dla okien narzędzi tekstowych i edytorów, wybierz opcję **Użyj wartości domyślnych**.

7. Wybierz przycisk **OK**.

### <a name="changing-the-colors-used-in-the-ide"></a>Zmiana kolorów używanych w środowisku IDE
 Możesz również zmienić domyślne kolory tekstu, wskaźników marginesów, białego znaku i elementów kodu w edytorze.

> [!NOTE]
> Aby użyć kolorów o dużym kontraście dla wszystkich okien aplikacji w systemie operacyjnym, naciśnij klawisze z lewej <strong>Alt +</strong>Strzałka w lewo **Shift + Print Screen**. Jeśli [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest otwarte, Zamknij i Otwórz ponownie, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Aby w pełni zaimplementować kolory o wysokim kontraście.

##### <a name="to-change-the-color-of-items-in-the-editor"></a>Aby zmienić kolor elementów w edytorze

1. W menu **Narzędzia** wybierz polecenie **Opcje**.

2. Wybierz **czcionki i kolory** z folderu **Environment** .

3. W obszarze **Pokaż ustawienia dla**wybierz **Edytor tekstu**.

4. Z **elementów wyświetlanych**wybierz element, którego ekran należy zmienić, na przykład **zwykły tekst**, **margines wskaźnika**, **widoczny odstęp**, **nazwa atrybutu HTML**lub **atrybut XML**.

5. Wybierz pozycję Ustawienia wyświetlania z następujących opcji: **pierwszy plan elementu**, **tło elementu**i **pogrubienie**.

6. Wybierz przycisk **OK**.

## <a name="toolbars"></a>Paski narzędzi
 Aby poprawić użyteczność i dostępność paska narzędzi, możesz dodać tekst do przycisków paska narzędzi.

#### <a name="to-assign-text-to-toolbar-buttons"></a>Aby przypisać tekst do przycisków paska narzędzi

1. W menu **Narzędzia** wybierz polecenie **Dostosuj**.

2. W oknie dialogowym **Dostosowywanie** wybierz kartę **polecenia** .

3. Wybierz pozycję **pasek narzędzi** , a następnie wybierz nazwę paska narzędzi zawierającego przycisk, dla którego ma być wyświetlany tekst.

4. Z listy wybierz polecenie, które ma zostać zmienione.

5. Wybierz **Modyfikuj zaznaczenie**.

6. Wybierz **obraz i tekst**.

#### <a name="to-modify-the-buttons-displayed-text"></a>Aby zmodyfikować wyświetlany tekst przycisku

1. Wybierz pozycję **Modyfikuj zaznaczenie**.

2. Obok **nazwy**w polu Wstaw Podaj nowy podpis dla wybranego przycisku.

## <a name="see-also"></a>Zobacz też
 [Funkcje ułatwień dostępu](../../ide/reference/accessibility-features-of-visual-studio.md) w zasobach programu Visual Studio [do projektowania dostępnych aplikacji](../../ide/reference/resources-for-designing-accessible-applications.md)
