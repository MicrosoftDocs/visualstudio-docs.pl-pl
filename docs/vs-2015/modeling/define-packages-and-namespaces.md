---
title: Definiowanie pakietów i przestrzeni nazw | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, namespaces
- UML, namespaces
- UML, packages
- UML model, packages
ms.assetid: 79147068-02d5-4b70-933d-f647c1da3829
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a949d72783f3d8ac1c2f0338e4ad7057f74653aa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766411"
---
# <a name="define-packages-and-namespaces"></a>Definiowanie pakietów i przestrzeni nazw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio *pakietu* jest kontenerem dla definicji elementów UML, takie jak klasy, przypadki użycia i składników. Pakiet może również zawierać innych pakietów.  
  
 W Eksploratorze modelu UML wszystkie definicje w pakiecie są zagnieżdżone poniżej pakietu. UML model jest rodzajem pakietu i stanowi główny drzewa.  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-topic"></a>W tym temacie  
 [Przestrzenie nazw](#Namespaces)  
  
 [Tworzenie i wyświetlanie pakietów](#Packages)  
  
 [Tworzenie modelu elementów wewnątrz pakietów](#Elements)  
  
 [Przenoszenie elementów do lub z pakietu](#Moving)  
  
 [Wklejanie elementów do pakietu](#Pasting)  
  
 [Importuj relacje między pakietami](#Import)  
  
 [Odwołania z jednej Namespace do innego](#References)  
  
 [Właściwości pakietów](#Properties)  
  
##  <a name="Namespaces"></a> Przestrzenie nazw  
 Pakiety są przydatne do oddzielania pracę w różnych obszarach. Każdy pakiet tak, określa przestrzeń nazw tak, aby nazwy, które są zdefiniowane w różnych pakietach nie były sprzeczne ze sobą.  
  
 Właściwość nazwy kwalifikowanej każdy element jest kwalifikowana nazwa pakietu, do której on należy, a następnie według nazwy własnego elementu. Na przykład, jeśli pakiet jest nazywany `MyPackage`, klasy w pakiecie odniesie nazwą kwalifikowaną, takich jak `MyPackage::MyClass`. Ponieważ każdy element znajduje się wewnątrz modelu, co kwalifikowana nazwa zaczyna się od nazwy modelu.  
  
 Modelu definiuje również przestrzeni nazw, dzięki czemu kwalifikowaną nazwę każdego elementu w modelu, który rozpoczyna się od nazwy modelu.  
  
 Przestrzenie nazw można również definiować w innych elementów modelu. Na przykład operacji należy do przestrzeni nazw, zdefiniowane przez jego klasy nadrzędnej, tak, aby jego nazwa kwalifikowana jest jak `MyModel ::MyPackage ::MyClass ::MyOperation`. W ten sam sposób akcję należy do przestrzeni nazw, zdefiniowane przez jego działania nadrzędnego.  
  
 Pakiety są kontenery. Jeżeli przeniesiesz lub usuniesz pakiet, klasy, pakiety i innymi, zdefiniowane wewnątrz niej również są przesyłane lub usunięty. Dotyczy to także inne elementy, które definiują przestrzenie nazw.  
  
##  <a name="Packages"></a> Tworzenie i wyświetlanie pakietów  
 Na diagramie klas UML lub w Eksploratorze modelu UML, można utworzyć pakietu.  
  
#### <a name="to-create-a-package-in-a-uml-class-diagram"></a>Aby utworzyć pakiet w diagramie klas UML  
  
1.  Otwórz diagram klas UML, lub Utwórz nową.  
  
2.  Kliknij przycisk **pakietu** narzędzia.  
  
3.  Kliknij w dowolnym miejscu na diagramie. Pojawi się nowy kształt pakietu.  
  
     Możesz kliknąć wewnątrz istniejącego pakietu, aby zagnieździć jeden pakiet w innym.  
  
4.  Wpisz nową nazwę dla pakietu.  
  
#### <a name="to-create-a-package-in-uml-model-explorer"></a>Aby utworzyć pakiet w Eksploratorze modelu UML  
  
1. Otwórz **Eksploratora modelu UML**. Na **architektury** menu wskaż **Windows**, a następnie kliknij przycisk **Eksploratora modelu UML**.  
  
2. Kliknij prawym przyciskiem myszy pakiet lub model, do którego chcesz dodać nowy pakiet.  
  
   > [!NOTE]
   >  Można zagnieżdżać pakietu wewnątrz innego pakietu.  
  
3. Wskaż **Dodaj** a następnie kliknij przycisk **pakietu**.  
  
    Nowy pakiet pojawia się w modelu.  
  
4. Wpisz nową nazwę dla pakietu.  
  
   Jeśli utworzono pakiet w Eksploratorze modelu UML, można wyświetlić je na diagramie klas UML. Można również wyświetlić pakiet na więcej niż jednym diagramie klas UML.  
  
#### <a name="to-show-an-existing-package-on-a-uml-class-diagram"></a>Aby wyświetlić istniejący pakiet na diagramie klas UML  
  
-   Przeciągnij pakietu z Eksploratora modelu UML na diagram klas.  
  
    > [!NOTE]
    >  Spowoduje to utworzenie widoku pakietu na tym diagramie. Go nie zawsze wyświetli wszystkie elementy pakiet zawiera. Aby wyświetlić wszystkie zawartości pakietu, należy go wyświetlić w Eksploratorze modelu UML.  
  
##  <a name="Elements"></a> Tworzenie modelu elementów wewnątrz pakietów  
 Istnieją cztery sposoby, w których można umieścić elementy modelu w pakiecie:  
  
- Dodaj nowy element do pakietu w Eksploratorze modelu UML.  
  
- Dodaj klasami i innymi typami do pakietów na diagramie klas UML.  
  
- Ustaw **LinkedPackage** właściwości diagramu, aby nowe elementy utworzone na diagramie są umieszczane w pakiecie, należy określić. Diagramy klas, diagramy składników i diagramy przypadków użycia może być połączony do pakietu w ten sposób.  
  
- Przesuń elementy do lub z pakietu w Eksploratorze modelu UML.  
  
  Element w pakiecie, który pojawia się poniżej pakietu w Eksploratorze modelu UML i jego kwalifikowana nazwa zaczyna się od nazwy kwalifikowanej pakietu. Aby wyświetlić kwalifikowana nazwa dowolnego elementu, kliknij prawym przyciskiem myszy element, a następnie kliknij przycisk **właściwości**. **Kwalifikowana nazwa** właściwość pojawia się w **właściwości** okna.  
  
#### <a name="to-create-an-element-in-a-package-in-uml-model-explorer"></a>Można utworzyć elementu w pakiecie w Eksploratorze modelu UML  
  
1.  Otwórz **Eksploratora modelu UML**. Na **widoku** menu wskaż **Windows inne**, a następnie kliknij przycisk **Eksploratora modelu UML**.  
  
2.  Kliknij prawym przyciskiem myszy pakiet lub model, do którego chcesz dodać nowy element.  
  
3.  Wskaż **Dodaj**, a następnie kliknij typ elementu, który chcesz dodać.  
  
     Poniżej pakietu pojawi się nowy element.  
  
4.  Wpisz nazwę dla nowego elementu.  
  
    > [!NOTE]
    >  Nowy element nie jest wyświetlana na dowolny diagram. Aby utworzyć widok nowego elementu, można przeciągnąć go z Eksploratora modelu UML na diagram. Diagram musi być typem, który będzie wyświetlany ten rodzaj elementu.  
  
#### <a name="to-create-an-element-in-a-package-on-a-uml-class-diagram"></a>Można utworzyć elementu w pakiecie na diagramie klas UML  
  
1.  Otwórz diagram klas, na której znajduje się pakiet.  
  
    -   Jeśli użytkownik jeszcze nie zostało to zrobione, należy utworzyć nowy pakiet.  
  
    -   Aby istniejącego pakietu są wyświetlane na diagramie klasy, można przeciągnąć pakiet z **Eksploratora modelu UML** na diagram klas.  
  
2.  Kliknij narzędzie do klasy, interfejsu, lub wyliczenia lub pakietu.  
  
3.  Kliknij pakiet, którym chcesz umieścić nowy element.  
  
     Nowy element pojawia się wewnątrz pakietu.  
  
#### <a name="to-create-all-the-elements-of-a-diagram-in-a-specified-package"></a>Aby utworzyć wszystkie elementy diagramu w określonym pakiecie  
  
1.  Tworzenie pakietu, jeśli użytkownik jeszcze nie zostało to zrobione.  
  
2.  Otwórz diagram składników, diagram przypadków użycia lub diagram klas UML.  
  
3.  Otwórz właściwości diagramu. Kliknij prawym przyciskiem myszy pustą część diagramu, a następnie kliknij przycisk **właściwości**.  
  
4.  W **połączone pakietu** właściwości, wybierz pakiet, który ma zawierać zawartość dla diagramu.  
  
5.  Utwórz nowe elementy na diagramie. Zostaną one umieszczone w pakiecie.  
  
    -   **Kwalifikowana nazwa** każdego elementu rozpoczyna się od nazwy kwalifikowanej pakietu.  
  
    -   W **Eksploratora modelu UML**, każdy element pojawią się w pakiecie.  
  
##  <a name="Moving"></a> Przenoszenie elementów do i z pakietów  
 Możesz przenieść jeden lub więcej elementów w lub poza nią pakiet.  
  
 Jeśli przenosisz pakietu, wszystko wewnątrz niej przenosi się z nim.  
  
#### <a name="to-move-an-element-into-or-out-of-a-package"></a>Aby przenieść element do lub z pakietu  
  
-   W Eksploratorze modelu UML przeciągnij element do lub z drzewa, w których główny jest pakietu.  
  
     Aby wyświetlić jego właścicielem pakiet lub model zmieni się kwalifikowana nazwa elementu.  
  
     \- lub —  
  
-   Na diagramie klasy przeciągnij element do kształtu pakiet.  
  
     Kwalifikowana nazwa elementu zostaną zmieniają się jej nowy pakiet będący właścicielem.  
  
    > [!NOTE]
    >  Jeśli przeciągniesz element z pakietu do pustą część diagramu, jej właścicielem pakietu nie zmienia się. Dzięki temu można utworzyć diagram pokazujący elementy z kilka pakietów, bez konieczności Pokaż pakiety, samodzielnie.  
  
##  <a name="Pasting"></a> Wklejanie elementów do pakietu  
 Element można wkleić do pakietu. Jeśli wklejasz grupą powiązanych elementów do pakietu, również można wkleić relacje między nimi.  
  
#### <a name="to-paste-elements-into-a-package-on-a-uml-class-diagram"></a>Aby wkleić elementów do pakietu na diagramie klas UML  
  
1.  Na diagramie klas UML wybierz wszystkie elementy, które mają zostać skopiowane. Kliknij prawym przyciskiem myszy jeden z nich, a następnie kliknij przycisk **kopiowania**.  
  
2.  Kliknij prawym przyciskiem myszy pakiet, a następnie kliknij przycisk **Wklej**.  
  
    > [!NOTE]
    >  Pakiet może być na innym diagramie.  
  
##  <a name="Import"></a> Importuj relacje między pakietami  
 Można zdefiniować importu relacja pakietów, za pomocą **zaimportować** narzędzia.  
  
 Importuj oznacza, że elementy zdefiniowane w pakiecie importowanych, które są elementy na końcu strzałkę relacji, efektywnie są również zdefiniowane importowania pakietu. Wszelkie elementy, których widoczność jest zdefiniowany jako **pakietu** będzie widoczny także w przypadku importowania pakietu.  
  
 Unikaj tworzenia pętli w relacjach importu.  
  
##  <a name="References"></a> Odwołania z jednej Namespace do innego  
 Jeśli chcesz odwołać się do elementu jeden pakiet z innym, musisz podać kwalifikowaną nazwę elementu.  
  
 Na przykład załóżmy, że pakiet `SalesCommon` definiuje typ `CustomerAddress`. W innym pakiecie `RestaurantSales`, aby zdefiniować typ `MealOrder`, który ma atrybut typu adresu odbiorcy. Dostępne są dwie opcje:  
  
-   Określ typ atrybutu za pomocą w pełni kwalifikowana nazwa `SalesCommon::CustomerAddress`. Należy wykonać tylko wtedy, gdy może `CustomerAddress` ma jego **widoczność** właściwością **publicznych**.  
  
-   Utwórz relację importu z `RestaurantSales` pakietu `SalesCommon` pakietu. Następnie można użyć `CustomerAddress` bez użycia nazwy kwalifikowanej.  
  
##  <a name="Properties"></a> Właściwości pakietów  
 Każdy pakiet ma następujące właściwości. Aby wyświetlić właściwości, kliknij prawym przyciskiem myszy pakiet, w diagramie lub w Eksploratorze modelu UML, a następnie kliknij przycisk **właściwości**.  
  
|Właściwość|Wartość domyślna|Opis|  
|--------------|-------------------|-----------------|  
|**Nazwa**|(Nowa nazwa)|Nazwa pakietu. Można go zmienić na diagramie lub w oknie dialogowym właściwości.|  
|**Kwalifikowana nazwa**|*Kontener* :: *nazwy pakietu*|Imię i nazwisko, prefiks według nazwy pakietu lub modelu, który zawiera ten pakiet. Aby uzyskać więcej informacji, zobacz [przestrzenie nazw](#Namespaces).|  
|**Profile**|(pusty)|Na liście profilów, połączone z tym pakietem. Te profile zawierają stereotypów, które mogą być stosowane do elementy wewnątrz pakietu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie modelu z profilami i stereotypami](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|  
|**Widoczność**|**Public**|Widoczność pakietu poza jej pakietu podrzędnego.|  
|**Elementy robocze**|(pusty)|Lista połączonych elementów roboczych. Aby uzyskać więcej informacji, zobacz [łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md).|  
|**Lokalizacja definicji**|(nazwa)|Nazwa pliku, w którym są przechowywane szczegóły pakietu. Pliki znajdują się wewnątrz **ModelDefinition** folderu projektu. Te informacje mogą być przydatne do celów kontroli źródła.|  
|**Opis**|(pusty)|Opis pakietu.|  
|**Stereotypy**|(pusty)|Stereotypów, które są stosowane do tego pakietu. Lista dostępnych Stereotypy jest ustalana profilów, które zostały wybrane dla tego pakietu i pakiety zawierające je. Aby uzyskać więcej informacji, zobacz [Dostosowywanie modelu z profilami i stereotypami](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|  
  
## <a name="how-packages-are-stored"></a>Jak są przechowywane pakietów  
 Podczas tworzenia nowego pakietu, nowy **.uml** plik zostanie utworzony w **ModelDefinition** folderu projektu. W modelu głównym, który jest również pakiet, jest również przechowywane **.uml** pliku.  
  
 Ponadto każdy diagram jest przechowywany w dwóch plikach, taki, który reprezentuje kształtach diagramu, a **.layout** pliku, który rejestruje pozycji kształtów.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy klas UML: Wytyczne dotyczące](../modeling/uml-class-diagrams-guidelines.md)   
 [Zarządzanie modelami i diagramami w ramach kontroli wersji](../modeling/manage-models-and-diagrams-under-version-control.md)
