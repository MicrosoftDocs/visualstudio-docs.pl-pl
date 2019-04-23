---
title: Instalowanie dokumentacji pomocy lokalnej
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer]
- updating local content [Help Viewer]
- Help Viewer, content installation source
- Help Viewer, updating local content
- Help Viewer, changing content installation source
- installing local content [Help Viewer]
- content installation source [Help Viewer]
- downloading content [Help Viewer]
- removing local content [Help Viewer]
- Help Viewer, removing local content
- Help Viewer, installing local content
- Help Viewer, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5576d1a7f66e11056240702f81e2f55edf65f5a0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073907"
---
# <a name="install-and-manage-local-content"></a>Instalowanie i zarządzać zawartością lokalną

Za pomocą Podglądu pomocy firmy Microsoft, mogą dodawania, usuwania, zaktualizować i przenieść zawartość pomocy, która jest zainstalowana na komputerze, aby zaspokajać potrzeby rozwoju oprogramowania.

Aby zarządzać zawartością na komputerze lokalnym, należy zalogować się przy użyciu konta z uprawnieniami administratora. Ponadto nie można zarządzać zawartością lokalną, jeśli pracujesz w środowisku przedsiębiorstwa, ponieważ administratorzy systemu mogą podjąć te decyzje dla danej organizacji. Aby uzyskać więcej informacji, zobacz [Podręcznik administratora programu Podgląd Pomocy](../help-viewer/administrator-guide.md).

## <a name="change-the-content-installation-source"></a>Zmiana źródła instalacji zawartości

Domyślnie Podgląd pomocy instaluje zawartość przy użyciu usług Microsoft online Services jako źródło. Możesz ogólnie nie należy zmieniać źródła zawartości, chyba że użytkownik pracuje w środowisku przedsiębiorstwa, dla którego administrator systemu już zainstalował zawartość w innej lokalizacji.

### <a name="to-change-the-content-installation-source"></a>Aby zmienić źródło zawartości instalacji

1. Na **zarządzanie zawartością** kartę, wybrać **dysku** przycisku opcji.

    > [!NOTE]
    > **Dysku** opcja jest niedostępna, jeśli administrator uniemożliwił Ci modyfikowanie źródła instalacji zawartości. Aby uzyskać więcej informacji, zobacz [Podręcznik administratora programu Podgląd Pomocy](../help-viewer/administrator-guide.md).

2. Wykonaj jedną z następujących czynności:

    - Wprowadź ścieżkę *.msha* plik lub adres URL punktu końcowego usługi.

    - Wybierz kolejno opcje Przeglądaj (**...** ) przycisk, aby przejść do *.msha* pliku.

    - Na liście wybierz wpis, który był używany ostatni.

## <a name="download-and-install-content-locally"></a>Pobieranie i instalowanie zawartości lokalnie

Jeżeli pobierzesz i zainstalujesz zawartość na komputerze lokalnym, możesz wyświetlić tematy, gdy nie masz dostępu do Internetu.

> [!IMPORTANT]
> Aby zainstalować zawartość, należy zalogować się przy użyciu konta z uprawnieniami administracyjnymi.

> [!NOTE]
> Jeśli programu Visual Studio IDE jest ustawiony na język inny niż angielski, można zainstalować zawartość w języku angielskim i/lub zlokalizowanej zawartości. Jednak żadnej zawartości pojawia się po zainstalowaniu tylko angielskiej wersji i **zawartości Zawrzyj w języku angielskim we wszystkich kartach nawigacji i żądaniach F1** pole wyboru w **Opcje podglądu** okno dialogowe zostanie wyczyszczona.

### <a name="to-download-and-install-content"></a>Aby pobrać i zainstalować zawartość

1. Wybierz **zarządzanie zawartością** kartę.

2. Na liście zawartości, wybierz opcję **Dodaj** łącze obok księgi lub ksiąg, które chcesz pobrać i zainstalować.

     Książka zostanie dodana do **oczekujące zmiany** listy, a szacowany rozmiar księgi lub ksiąg, które określiłeś, zostanie wyświetlone poniżej tej listy. Ponieważ niektóre książki mają wspólne tematy, całkowity rozmiar wiele książek może być mniejszy niż suma wielkości każdej z książek.

3. Wybierz **aktualizacji** przycisku.

     Księgi lub ksiąg, które można określić są instalowane wraz z wszelkimi aktualizacjami książek, które mają już na tym komputerze. Czasy instalacji różnią się, ale mogą wyświetlić postęp na pasku stanu.

## <a name="remove-local-content"></a>Usuwanie zawartości lokalnej

Można zaoszczędzić miejsce na dysku przez usunięcie niepożądanych elementów ze swojego komputera.

> [!IMPORTANT]
> Musi mieć uprawnienia administracyjne, aby usunąć zawartość.

> [!NOTE]
> Żadna zawartość jest wyświetlana, jeśli programu Visual Studio IDE jest ustawiony na język inny niż angielski, usuniesz zlokalizowaną zawartości i **zawartości Zawrzyj w języku angielskim we wszystkich kartach nawigacji i żądaniach F1** pole wyboru w **Opcje podglądu** okno dialogowe zostanie wyczyszczona.

### <a name="to-remove-content"></a>Aby usunąć zawartość

1. Wybierz **zarządzanie zawartością** kartę.

2. Na liście zawartości, wybierz opcję **Usuń** łącze obok księgi lub ksiąg, które chcesz usunąć.

     Książka zostanie dodana do **oczekujące zmiany** listy.

3. Wybierz **aktualizacji** przycisku.

     Księgi lub ksiąg, określonych przez użytkownika są usuwane z komputera.

## <a name="update-local-content"></a>Aktualizowanie zawartości lokalnej

Pasek stanu wskazuje, kiedy są dostępne aktualizacje zainstalowanej zawartości.

> [!IMPORTANT]
> Jeśli chcesz **podglądu pomocy** Aby automatycznie sprawdzać aktualizacje w trybie online, należy otworzyć **Opcje podglądu** okno dialogowe, a następnie wybierz pozycję **przejdź do trybu online, aby sprawdzić, czy są dostępne aktualizacje zawartości**pole wyboru.

### <a name="to-update-local-content"></a>Aby zaktualizować zawartość lokalną

- W prawym dolnym rogu paska stanu, wybierz **kliknij tutaj, aby pobrać teraz** łącza.

Czasy aktualizacji mogą się różnić, ale możesz wyświetlić postęp aktualizacji, na pasku stanu.

## <a name="move-local-content"></a>Przenoszenie zawartości lokalnej

Przenosząc zainstalowaną zawartość z komputera lokalnego do udziału sieciowego lub na inną partycję na komputerze lokalnym, można zaoszczędzić miejsce na dysku.

> [!IMPORTANT]
> Aby przenieść zawartość, należy zalogować się przy użyciu konta z uprawnieniami administracyjnymi.

### <a name="to-move-local-content"></a>Aby przenieść zawartość lokalną

1. Na **zarządzanie zawartością** kartę, wybrać **przenieść** przycisku w obszarze **ścieżkę lokalną Store**.

     **Przenoszenie zawartości** zostanie otwarte okno dialogowe.

2. W **do** pola tekstowego, wprowadzić inną lokalizację zawartości, a następnie wybierz **OK** przycisku.

3. Wybierz **Zamknij** przycisk po przeniesieniu zawartości.

## <a name="see-also"></a>Zobacz także

- [Podgląd Pomocy firmy Microsoft](../help-viewer/overview.md)