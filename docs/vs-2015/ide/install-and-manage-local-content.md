---
title: Instalowanie i zarządzać zawartością lokalną | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer 2.0]
- updating local content [Help Viewer 2.0]
- Help Viewer 2.0, content installation source
- Help Viewer 2.0, updating local content
- Help Viewer 2.0, changing content installation source
- installing local content [Help Viewer 2.0]
- content installation source [Help Viewer 2.0]
- downloading content [Help Viewer 2.0]
- removing local content [Help Viewer 2.0]
- Help Viewer 2.0, removing local content
- Help Viewer 2.0, installing local content
- Help Viewer 2.0, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a6e52c9a34b5fc6ea487cffd1728a525dc5a0984
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54766227"
---
# <a name="install-and-manage-local-content"></a>Instalowanie zawartości lokalnej i zarządzanie nią
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą Podglądu pomocy firmy Microsoft, możesz dodać, usunąć, aktualizacji i przenieść zawartość pomocy, która jest zainstalowana na komputerze, aby zaspokajać potrzeby rozwoju oprogramowania.  
  
 Aby zarządzać zawartością na komputerze lokalnym, należy zalogować się przy użyciu konta z uprawnieniami administracyjnymi. Ponadto nie można zarządzać zawartością lokalną, jeśli pracujesz w środowisku przedsiębiorstwa, ponieważ administratorzy systemu mogą podjąć te decyzje dla danej organizacji. Aby uzyskać więcej informacji, zobacz [Podręcznik administratora programu Podgląd Pomocy](../ide/help-viewer-administrator-guide.md).  
  
## <a name="changing-the-content-installation-source"></a>Zmiana źródła instalacji zawartości  
 Domyślnie Podgląd pomocy instaluje zawartość przy użyciu usług Microsoft online Services jako źródło. Możesz ogólnie nie należy zmieniać źródła zawartości, chyba że użytkownik pracuje w środowisku przedsiębiorstwa, dla którego administrator systemu już zainstalował zawartość w innej lokalizacji.  
  
#### <a name="to-change-the-content-installation-source"></a>Aby zmienić źródło zawartości instalacji  
  
1.  Na **zarządzanie zawartością** kartę, wybrać **dysku** przycisku opcji.  
  
    > [!NOTE]
    >  **Dysku** opcji nie będzie dostępny, jeśli administrator uniemożliwił Ci modyfikowanie źródła instalacji zawartości. Aby uzyskać więcej informacji, zobacz [Podręcznik administratora programu Podgląd Pomocy](../ide/help-viewer-administrator-guide.md).  
  
2.  Wykonaj jedną z następujących czynności:  
  
    -   Wprowadź ścieżkę do pliku .msha lub adres URL punktu końcowego usługi.  
  
    -   Wybierz kolejno opcje Przeglądaj (**...** ) przycisk, aby przejść do pliku .msha.  
  
    -   Na liście wybierz wpis, który był używany ostatni.  
  
## <a name="download-and-install-content-locally"></a>Pobieranie i instalowanie zawartości lokalnie  
 Jeżeli pobierzesz i zainstalujesz zawartość na komputerze lokalnym, można wyświetlić tematy bez połączenia internetowego.  
  
> [!IMPORTANT]
>  Aby zainstalować zawartość, należy zalogować się przy użyciu konta z uprawnieniami administracyjnymi.  
  
 Jeśli programu Visual Studio IDE jest ustawiony na język inny niż angielski, można zainstalować zawartość w języku angielskim i/lub zlokalizowanej zawartości. Jednakże, wyświetli się żadna zawartość, po zainstalowaniu tylko angielskiej wersji i **zawartości Zawrzyj w języku angielskim we wszystkich kartach nawigacji i żądaniach F1** pole wyboru w **Opcje podglądu** okno dialogowe zostanie wyczyszczona.  
  
#### <a name="to-download-and-install-content"></a>Aby pobrać i zainstalować zawartość  
  
1.  Wybierz **zarządzanie zawartością** kartę.  
  
2.  Na liście zawartości, wybierz opcję **Dodaj** łącze obok księgi lub ksiąg, które chcesz pobrać i zainstalować.  
  
     Książka zostanie dodana do **oczekujące zmiany** listy, a szacowany rozmiar księgi lub ksiąg, które określiłeś, zostanie wyświetlone poniżej tej listy. Ponieważ niektóre książki mają wspólne tematy, całkowity rozmiar wiele książek może być mniejszy niż suma wielkości każdej z książek.  
  
3.  Wybierz **aktualizacji** przycisku.  
  
     Księgi lub ksiąg, które można określić są instalowane wraz z wszelkimi aktualizacjami książek, które mają już na tym komputerze. Czasy instalacji różnią się, ale mogą wyświetlić postęp na pasku stanu.  
  
## <a name="removing-local-content"></a>Usuwanie zawartości lokalnej  
 Można zaoszczędzić miejsce na dysku przez usunięcie niepożądanych elementów ze swojego komputera.  
  
> [!IMPORTANT]
>  Musi mieć uprawnienia administracyjne, aby usunąć zawartość.  
  
 Wyświetli się żadna zawartość, jeśli programu Visual Studio IDE jest ustawiony na język inny niż angielski, usuniesz zlokalizowaną zawartości i **zawartości Zawrzyj w języku angielskim we wszystkich kartach nawigacji i żądaniach F1** pole wyboru w **Opcje podglądu**  okno dialogowe zostanie wyczyszczona.  
  
#### <a name="to-remove-content"></a>Aby usunąć zawartość  
  
1.  Wybierz **zarządzanie zawartością** kartę.  
  
2.  Na liście zawartości, wybierz opcję **Usuń** łącze obok księgi lub ksiąg, które chcesz usunąć.  
  
     Książka zostanie dodana do **oczekujące zmiany** listy.  
  
3.  Wybierz **aktualizacji** przycisku.  
  
     Księgi lub ksiąg, określonych przez użytkownika są usuwane z komputera.  
  
## <a name="updating-local-content"></a>Aktualizowanie zawartości lokalnej  
 Pasek stanu wskazuje, kiedy są dostępne aktualizacje zainstalowanej zawartości.  
  
> [!IMPORTANT]
>  Jeśli chcesz, aby Podgląd pomocy automatycznie sprawdzaj aktualizacje w trybie online, należy otworzyć **Opcje podglądu** okno dialogowe, a następnie wybierz pozycję **przejdź do trybu online, aby sprawdzić, czy są dostępne aktualizacje zawartości** pole wyboru.  
  
#### <a name="to-update-local-content"></a>Aby zaktualizować zawartość lokalną  
  
- W prawym dolnym rogu paska stanu, wybierz **kliknij tutaj, aby pobrać teraz** łącza.  
  
  Czasy aktualizacji mogą się różnić, ale możesz wyświetlić postęp aktualizacji, na pasku stanu.  
  
## <a name="moving-local-content"></a>Przenoszenie zawartości lokalnej  
 Przenosząc zainstalowaną zawartość z komputera lokalnego do udziału sieciowego lub na inną partycję na komputerze lokalnym, można zaoszczędzić miejsce na dysku.  
  
> [!IMPORTANT]
>  Aby przenieść zawartość, należy zalogować się przy użyciu konta z uprawnieniami administracyjnymi.  
  
#### <a name="to-move-local-content"></a>Aby przenieść zawartość lokalną  
  
1.  Na **zarządzanie zawartością** kartę, wybrać **przenieść** przycisku w obszarze **ścieżkę lokalną Store**.  
  
     **Przenoszenie zawartości** zostanie otwarte okno dialogowe.  
  
2.  W **do** pola tekstowego, wprowadzić inną lokalizację zawartości, a następnie wybierz **OK** przycisku.  
  
3.  Wybierz **Zamknij** przycisk po przeniesieniu zawartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Podgląd Pomocy firmy Microsoft](../ide/microsoft-help-viewer.md)
