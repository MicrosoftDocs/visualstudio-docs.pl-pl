---
title: Zarządzanie modelami i diagramami w ramach kontroli wersji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, version control
ms.assetid: ca6443e3-6d11-4da8-aae7-ca7dcc410076
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30b13610cc59b8a0225e52abf47f9a4f2cc97d1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657579"
---
# <a name="manage-models-and-diagrams-under-version-control"></a>Zarządzanie modelami i diagramami w ramach kontroli wersji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zarządzanie różnymi wersjami projektów i diagramów modelowania, w tym mapy kodu (pliki dgml), przy użyciu funkcji [kontroli wersji Team Foundation lub git](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314); za pomocą Team Foundation Server lokalnych lub w chmurze z Visual Studio Team Services.

 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!IMPORTANT]
> Należy zachować ostrożność, gdy kilku użytkowników pracuje nad tym samym projektem modelowania. Dowiedz się, w jaki sposób można [organizować modele w średnich lub dużych projektach](../modeling/structure-your-modeling-solution.md).

## <a name="ModelingProjects"></a>Pliki w projekcie modelowania
 Więcej niż jeden użytkownik może korzystać z projektu modelowania w tym samym czasie, pod warunkiem, że działają na różnych plikach.

 Aby uniknąć lub rozwiązać konflikty między zmianami wprowadzonymi przez różnych użytkowników, ważne jest, aby zrozumieć, jak model jest przechowywany w plikach.

- Każdy pakiet jest przechowywany w osobnym pliku **UML** , który znajduje się w folderze projektu **ModelDefinition** . Model ma również plik **. UML** . Jeśli jeden z tych plików zostanie usunięty lub uszkodzony, odpowiedni pakiet lub model zostanie utracony.

- Każdy diagram jest przechowywany w dwóch plikach. Na przykład Diagram klas ma:

  - **DiagramName. classdiagram** — Jeśli ten plik zostanie usunięty lub uszkodzony, diagram zostanie utracony, ale klasy i skojarzenia, które pozostały nadal będą w modelu i mogą być widoczne w EKSPLORATORZE modelu UML.

  - **DiagramName. classdiagram. layout** — Jeśli ten plik zostanie usunięty, nadal będzie wyświetlany diagram, ale utracisz swoje rozmiary i położenia. Każdy plik układu jest zależny od pliku diagramu. Aby je wyświetlić, kliknij [+] obok pliku diagramu w Eksplorator rozwiązań.

> [!NOTE]
> Ważne jest, aby zachować spójność plików. Na przykład w przypadku korzystania z kontroli źródła w celu wycofania zmian w pliku. UML należy wycofać odpowiednie zmiany w plikach diagramu i układu. Elementy reprezentowane w. plik \*diagram zostanie utracony, jeśli nie są również reprezentowane w pliku. UML.

## <a name="Shared"></a>Praca nad udostępnionymi projektami modelowania
 Aby zminimalizować konflikty między współbieżną pracy w różnych częściach projektu:

- Podziel projekt modelowania na pakiety reprezentujące różne obszary pracy. Przenieś cały model do pakietów zamiast opuszczania go w modelu głównym. Aby uzyskać więcej informacji, zobacz [Definiowanie pakietów i przestrzeni nazw](../modeling/define-packages-and-namespaces.md).

- Różni użytkownicy nie mogą jednocześnie korzystać z tego samego pakietu lub diagramu.

- Jeśli używasz profilów, upewnij się, że wszyscy mają zainstalowane te same profile. Zobacz [Dostosowywanie modelu za pomocą profilów i stereotypów](../modeling/customize-your-model-with-profiles-and-stereotypes.md).

- Aby mieć pewność, że zmienisz tylko pakiet, nad którym pracujesz:

  - Ustaw właściwość **LinkedPackage** klasy UML, składnika lub przypadku użycia.

  - W Eksploratorze modelu UML przeciągnij działanie lub interakcję z pakietem zaraz po jego utworzeniu. Ten element będzie wyświetlany w Eksploratorze modelu UML podczas tworzenia pierwszego węzła w diagramie aktywności lub sekwencji.

- Aby ułatwić śledzenie pakietów, Zmień nazwę plików pakietu, aby odzwierciedlały rzeczywiste nazwy pakietów.

- W [!INCLUDE[esprscc](../includes/esprscc-md.md)] zawsze **sprawdzaj** i **Pobieraj najnowsze wersje** na pełnym projekcie modelowania, nigdy nie na pojedynczych plikach.

- Zawsze należy wykonać operację **pobrania** bezpośrednio przed zaewidencjonowaniem projektu modelowania.

- Zawsze zamykaj wszystkie diagramy przed wykonaniem operacji **Get** .

    > [!NOTE]
    > Jeśli po wykonaniu operacji **Get**plik jest otwarty, a operacja spowoduje wprowadzenie zmian lokalnych, zostanie wyświetlony monit o ponowne załadowanie pliku. W takim przypadku kliknij przycisk **nie**, a następnie ponownie załaduj cały projekt. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu modelowania, kliknij polecenie **Zwolnij projekt**, a następnie kliknij polecenie **Załaduj ponownie projekt**.

### <a name="Exclusive"></a>Zmiany wymagające wyłącznego dostępu do modelu
 Przed wprowadzeniem następujących rodzajów zmian upewnij się, że masz blokadę wyewidencjonowania dla całego projektu.

- Zmiana nazwy lub usuwanie elementów, do których odwołuje się inne pakiety.

- Zmiana właściwości relacji obejmujących wiele pakietów.

- Aby dowiedzieć się więcej o blokadach wyewidencjonowywania, zobacz [Wyewidencjonowywanie i edytowanie plików](https://msdn.microsoft.com/library/eb404d63-c448-4994-9416-3e6d50ec554a).

##### <a name="to-move-a-diagram-file-in-or-out-of-a-project-folder"></a>Aby przenieść plik diagramu do lub z folderu projektu

1. Uruchom **wiersz polecenia programisty dla programu Visual Studio**.

2. Użyj **TF Zmień nazwę** , aby przenieść plik diagramu i jego plik **. layout** :

     `tf rename sourcePath targetPath`

3. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy plik, a następnie kliknij pozycję **Wyklucz z projektu**.

4. Dodaj plik do folderu docelowego.

     W Eksplorator rozwiązań kliknij prawym przyciskiem myszy folder docelowy lub projekt, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **istniejący element**. W oknie dialogowym Wybierz plik diagramu, a następnie kliknij przycisk **Dodaj**. Plik układu zostanie dodany automatycznie.

    > [!NOTE]
    > Nie można przenieść pliku do innego projektu.

## <a name="Merging"></a>Scalanie zmian w plikach i diagramach modelu
 Gdy więcej niż jeden użytkownik pracował nad modelem jednocześnie, [!INCLUDE[esprscc](../includes/esprscc-md.md)] wyświetli monit o scalenie zmian w plikach modelu. Praca nad oddzielnymi projektami, zgodnie z opisem w poprzednich sekcjach, spowoduje uniknięcie większości scaleń. Zazwyczaj pozostałe konflikty mogą być bezpiecznie scalane automatycznie. Następujące rodzaje zmian nie powinny mieć żadnego trudności:

- Typy linii życia. Po dodaniu linii życia do interakcji (diagramu sekwencji) jego typ jest przechowywany w modelu głównym, chyba że utworzono linię życia z istniejącego typu.

- Nowe działania i interakcje są początkowo przechowywane w modelu głównym.

- Dodawanie elementów i relacji.

- Zmiana nazwy lub usuwanie elementów, do których odwołuje się tylko w ramach własnego pakietu.

## <a name="see-also"></a>Zobacz też
 [Analizowanie i modelowanie](../modeling/analyze-and-model-your-architecture.md) [modeli udostępniania architektury i eksportowanie diagramów](../modeling/share-models-and-exporting-diagrams.md)
