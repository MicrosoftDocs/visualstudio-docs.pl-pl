---
title: Zarządzanie modelami i diagramami w ramach kontroli wersji | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, version control
ms.assetid: ca6443e3-6d11-4da8-aae7-ca7dcc410076
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2a7ba74c18097f7eb4b2f8ff50780dfd5ffb57df
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080323"
---
# <a name="manage-models-and-diagrams-under-version-control"></a>Zarządzanie modelami i diagramami w ramach kontroli wersji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zarządzać różne wersje usługi projektów i diagramów modelowania, łącznie z mapy kodu (pliki .dgml) za pomocą [Użyj kontroli wersji serwera Team Foundation lub Git](http://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314); albo z lokalnego serwera Team Foundation Server lub w chmurze za pomocą Visual Studio Team Services.  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!IMPORTANT]
>  Kilku użytkowników pracuje nad tym samym projekcie modelowania, należy zachować ostrożność. Dowiedz się, jak można [organizowania modeli w średnich i dużych projektach](../modeling/structure-your-modeling-solution.md).  
  
## <a name="ModelingProjects"></a> Pliki w projekcie modelowania  
 Więcej niż jeden użytkownik może pracować nad projektem modelowania w tym samym czasie, pod warunkiem, że działają na różnych plikach.  
  
 Aby uniknąć lub rozwiązać konflikty między zmianami wprowadzanymi przez różnych użytkowników, ważne jest zrozumienie, jak model jest przechowywany w plikach.  
  
- Każdy pakiet jest przechowywany w osobnym **.uml** pliku, który jest przechowywany w **ModelDefinition** folderu projektu. Ten model ma również **.uml** pliku. Jeśli jeden z tych plików jest usunięty lub uszkodzony, odpowiedni pakiet lub model zostaną utracone.  
  
- Każdy diagram jest przechowywany w dwóch plikach. Na przykład diagram klas ma:  
  
    - **DiagramName.classdiagram** — Jeśli ten plik zostaje usunięty lub uszkodzony, diagram zostanie utracony, ale klasy i stowarzyszenia będą nadal istnieć w modelu i będą widoczne w Eksploratorze modelu UML.  
  
    - **DiagramName.classdiagram.layout** — Jeśli ten plik zostanie usunięty, kształty będą nadal pojawiać się na diagramie, ale utracą swoje rozmiary i położenie. Każdy plik układu jest zależny od pliku diagramu. Aby sprawdzić, kliknij przycisk [+] obok pliku diagramu w Eksploratorze rozwiązań.  
  
> [!NOTE]
>  Jest to ważne, aby zachować spójność między plikami. Na przykład, jeśli używasz kontroli źródła do wycofania zmian w pliku .uml, należy wycofać odpowiednie zmiany. * diagram i .layout pliki w tym samym czasie. Elementy reprezentowane w. \*plik diagramu zostaną utracone, jeśli nie są one również reprezentowane w pliku .uml.  
  
## <a name="Shared"></a> Praca na udostępnionych projektach modelowania  
 Aby zminimalizować konflikty między równoczesną pracą na różnych części projektu:  
  
- Podziel projekt modelowania na pakiety reprezentujące różne obszary pracy. Przenieś cały model do pakietów zamiast pozostawić go w modelu głównym. Aby uzyskać więcej informacji, zobacz [Definiowanie pakietów i przestrzeni nazw](../modeling/define-packages-and-namespaces.md).  
  
- Różni użytkownicy nie powinien pracować na tym samym pakiecie lub diagramie w tym samym czasie.  
  
- Jeśli używasz profilów, upewnij się, że wszyscy mają zainstalowane te same profile. Zobacz [Dostosowywanie modelu z profilami i stereotypami](../modeling/customize-your-model-with-profiles-and-stereotypes.md).  
  
- Aby ułatwić, upewnij się, że zmieniasz tylko pakiet, który użytkownik pracuje na:  
  
    - Ustaw **LinkedPackage** właściwość klasy, składnika lub diagram przypadków użycia UML.  
  
    - W Eksploratorze modelu UML przeciągnij działanie lub interakcję do pakietu natychmiast po jej utworzeniu. Element ten pojawi się w Eksploratorze modelu UML podczas tworzenia pierwszego węzła w diagramie sekwencji lub działania.  
  
- Aby ułatwić śledzenie pakietów, Zmień nazwę plików pakietu, aby odzwierciedlić rzeczywiste nazwy pakietów.  
  
- W [!INCLUDE[esprscc](../includes/esprscc-md.md)], zawsze wykonuj **Zaewidencjonuj** i **Pobierz najnowszą wersję** operacji na pełnym projekcie modelowania, nigdy na poszczególnych plikach.  
  
- Zawsze wykonuj **uzyskać** operacji natychmiast, przed zaewidencjonowaniem projektu modelowania.  
  
- Zawsze zamykaj wszystkie diagramy przed wykonaniem **uzyskać** operacji.  
  
    > [!NOTE]
    >  Jeśli plik jest otwarty podczas wykonywania **uzyskać**, i operacja powoduje zmiany lokalne, a następnie zostanie wyświetlony monit, aby ponownie załadować plik. W tym przypadku kliknij **nie**, a następnie ponownie załaduj pełen projekt. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy modelowania węzła projektu, kliknij przycisk **Zwolnij projekt**, a następnie kliknij przycisk **Załaduj ponownie projekt**.  
  
### <a name="Exclusive"></a> Zmiany wymaganie wyłącznego dostępu do modelu  
 Zanim dokonasz następujących rodzajów zmian, upewnij się, że masz blokadę Wyewidencjonuj dla całego projektu.  
  
- Zmiana nazwy lub usuwanie elementów, które są wywoływane z innych pakietów.  
  
- Zmiana właściwości relacji, które wykraczają poza pakiet.  
  
- Aby dowiedzieć się o blokadach wyewidencjonowania, zobacz [Sprawdź out i edytować pliki](http://msdn.microsoft.com/library/eb404d63-c448-4994-9416-3e6d50ec554a).  
  
##### <a name="to-move-a-diagram-file-in-or-out-of-a-project-folder"></a>Aby przenieść plik diagramu do lub z folderu projektu  
  
1. Rozpocznij **wiersz polecenia programisty dla programu Visual Studio**.  
  
2. Użyj **zmienić tf** do przenoszenia pliku diagramu i jego **.layout** pliku:  
  
     `tf rename sourcePath targetPath`  
  
3. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik, a następnie kliknij przycisk **Wyklucz z projektu**.  
  
4. Dodaj plik do folderu docelowego.  
  
     W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy folder docelowy lub projekt, wskaż opcję **Dodaj**, a następnie kliknij przycisk **istniejący element**. W oknie dialogowym Wybierz plik diagramu, a następnie kliknij przycisk **Dodaj**. Plik układu zostanie dodany automatycznie.  
  
    > [!NOTE]
    >  Nie można przenieść pliku do innego projektu.  
  
## <a name="Merging"></a> Scalanie zmian w plikach i diagramach modelu  
 Po więcej niż jeden użytkownik pracował w modelu jednocześnie, [!INCLUDE[esprscc](../includes/esprscc-md.md)] wyświetli monit o scalenie zmian w plikach modelu. Praca nad osobnymi projektami zgodnie z opisem w poprzednich sekcjach pozwoli uniknąć większości scaleń. Zwykle pozostałe konflikty mogą być bezpiecznie scalane automatycznie. Następujące rodzaje zmian, powinny powodować żadnych trudności:  
  
- Typy linii życia. Po dodaniu linii życia do interakcji (diagram sekwencji), jego typ jest magazynowany w modelu głównym, chyba że utworzono linii życia z istniejącego typu.  
  
- Nowe działania i interakcje są początkowo przechowywane w modelu głównym.  
  
- Dodawanie elementów i relacji.  
  
- Zmiana nazwy lub usuwanie elementów, które są wywoływane tylko w ramach własnego pakietu.  
  
## <a name="see-also"></a>Zobacz też  
 [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)   
 [Udostępnianie modeli i eksportowanie diagramów](../modeling/share-models-and-exporting-diagrams.md)
