---
title: Nieobsługiwane edycje w języku Visual Basic, Edytuj i Kontynuuj | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], unsupported method and property body edits
ms.assetid: 9b8fdc41-a193-49ad-ad72-dfcadd46f4b3
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc6e7a5d1d72464849bff20be066ea70e8264623
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787903"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Nieobsługiwane edycje funkcji Edytuj i kontynuuj programu Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytuj i Kontynuuj les zatrzymują wykonywanie programu w trybie przerwania, wprowadzić zmiany na wykonywanie kodu i wznowić wykonywanie programu przy użyciu nowo zarejestrowanych zmian. Kod deklaratywny zmian w strukturze publiczne klasy zwykle są niedozwolone, ale wiele zmian, które można wprowadzać do metody, właściwości treści lub prywatnej deklaracje w obrębie klasy są dozwolone.  
  
 Jeśli potrzebujesz wprowadzić zmianę, która nie jest obsługiwana, musi zatrzymać debugowanie, wprowadzić zmiany i rozpocznij nową sesję debugowania.  
  
###  <a name="BKMK_MethodandPropertyBodyEdits"></a> Metody i właściwości treści edycji  
 **Nieobsługiwane zmiany statyczne zmienne lokalne**: Dodawanie lub aktualizowanie zmiennej lokalnej lub usuwanie zmiennej lokalnej statycznej, jeśli spowodowałoby błąd kompilacji.  
  
 **Nieobsługiwane zmiany do typów ogólnych**: zmiany metody rodzajowej, samego lub treści metody ogólne nie są obsługiwane. Podczas tworzenia wystąpienia typu ogólnego lub połączeń do istniejących metod ogólnych mogą być dodane, usunięte lub zmienione.  
  
 **Inne nieobsługiwane zmiany**  
  
-   Zmiana instrukcji wywołania metody, która znajduje się w stosie wywołań.  
  
-   Dodawanie `Try...Catch` bloku, gdy wskaźnik instrukcji kończy się w `Catch` bloku lub `Finally` bloku.  
  
-   Usuwanie `Try...Catch` bloku, gdy wskaźnik instrukcji jest w `Catch`bloku lub `Finally` bloku.  
  
-   Dodawanie `Using` bloku wokół bieżący wskaźnik instrukcji.  
  
-   Dodawanie `SynchLock` bloku wokół bieżący wskaźnik instrukcji.  
  
###  <a name="BKMK_AttributeEdits"></a> Zmiany atrybutów  
 Edytuj i Kontynuuj nie obsługuje modyfikowania atrybutów. Ściślej mówiąc, Edytuj i Kontynuuj nie obsługuje następujące zmiany:  
  
-   Definiowanie, edytowanie lub usuwanie tworzy się klasę atrybutów.  
  
-   Dodawanie atrybutu.  
  
-   Edytowanie lub usuwanie istniejącego atrybutu.  
  
###  <a name="BKMK_ClassDeclarationEdits"></a> Edycje deklaracji klasy  
 Większość zmian deklaracje klas nie są dozwolone przez Edytuj i Kontynuuj w trybie przerwania. Ściślej mówiąc, Edytuj i Kontynuuj nie obsługuje następujące zmiany:  
  
-   Zmiana nazwy, usuwanie lub zmiana dziedziczenia istniejącej klasy.  
  
-   Implementowanie nowy interfejs lub usuwanie implementacji interfejsu.  
  
-   Zmiana modyfikatorów klasy.  
  
-   Dodawanie, zmienianie lub usuwanie `ComClass` stanu.  
  
-   Edytowanie żadnych deklaracji klasy ogólnej.  
  
###  <a name="BKMK_ClassMemberDeclarationEdits"></a> Edycje deklaracji elementu członkowskiego klasy  
 Zmiany w deklaracji elementu członkowskiego są niedozwolone w większości Edytuj i Kontynuuj przypadków. Na przykład nie można zmienić podpis lub poziom dostępu członka, a nie można całkowicie usunąć członków, jeśli spowodowałoby błąd kompilacji. Ściślej mówiąc, Edytuj i Kontynuuj nie obsługuje następujące zmiany:  
  
-   Przesłanianie istniejącą zmienną elementu członkowskiego przez zadeklarowanie globalna lub zmiennej składowej o takiej samej nazwie w bloku zawierającego.  
  
-   Przesłanianie zmiennej lokalnej statycznej przez zadeklarowanie nowego wystąpienia wewnątrz bloku.  
  
-   Usuwanie programów obsługi zdarzeń. Dodawanie obsługi zdarzeń jest dozwolone.  
  
-   Dodawanie nowej przeciążania operacji właściwości lub metody, chyba że właściwość lub metoda jest `Private` i nie ma żadnych wystąpień z nazwą w żadnej aktywnej instrukcji.  
  
-   Dodawanie lub usuwanie `WithEvents` klauzuli w zmiennej składowej.  
  
-   Usuwanie członka.  
  
-   Zmiana właściwości lub metody deklaracji można zatrzymać Implementowanie interfejsu.  
  
-   Edytowanie dowolną metodę, która używa typów ogólnych.  
  
-   Zmienianie podpisu lub zwracany typ nieprywatny właściwości lub metody.  
  
-   Zastępowanie i przesłanianie składowej w klasie bazowej.  
  
-   Dodawanie nowego pola w dowolnej klasy oznaczone `SequentialLayout` lub `ExplicitLayout`.  
  
-   Zmiana `MustInherit` lub `NotOverridable` stan metody.  
  
-   Zmiana modyfikatory dostępu do właściwości lub metody.  
  
-   Zmiana typu lub stanu pola tylko do odczytu.  
  
-   Zmienianie pola publiczne.  
  
###  <a name="BKMK_CompilerOptionEdits"></a> Edycje — opcja kompilatora  
 Podczas korzystania z Edytuj i Kontynuuj w trybie przerwania, nie można zmienić, Dodaj lub usuń następujące opcje kompilatora:  
  
-   **Option Strict**  
  
-   **Option Explicit**  
  
-   **Option Compare**  
  
###  <a name="BKMK_ConstantsEdits"></a> Edycje — stałe  
 Zmiany do stałych w trybie Edytuj i Kontynuuj są bardzo ograniczona. Ściślej mówiąc, Edytuj i Kontynuuj nie obsługuje następujące zmiany:  
  
-   Dodawanie lub aktualizowanie zmiennej stałej.  
  
-   Zmiana typu lub wartości stałej.  
  
-   Usuwanie stałą.  
  
###  <a name="BKMK_DelegateandEventDeclarationEdits"></a> Delegat, edycje deklaracja zdarzenia  
 Niektóre zmiany delegaci i zdarzenia nie są dozwolone w trybie Break, Edytuj i Kontynuuj. Ściślej mówiąc, Edytuj i Kontynuuj nie obsługuje następujące zmiany:  
  
-   Zmienianie lub usuwanie definicji delegata.  
  
-   Usuwanie zdarzenie.  
  
###  <a name="BKMK_EnumerationEdits"></a> Wyliczenie edycji  
 Zmiany wyliczenia (`Enums`), Edytuj i Kontynuuj nie są dozwolone w trybie przerwania. Ściślej mówiąc, Edytuj i Kontynuuj nie obsługuje następujące zmiany:  
  
-   Modyfikowanie bazowego typu `Enum`.  
  
-   Dodawanie, zmienianie lub usuwanie `Enum` elementu członkowskiego.  
  
-   Zmiana modyfikator dostępu elementu `Enum`.  
  
###  <a name="BKMK_ExternalDeclarationsEdits"></a> Deklaracje zewnętrzne zmiany  
 Ogólnie rzecz biorąc nie można zmienić deklaracje zewnętrzne metody podczas operacji Edytuj i Kontynuuj. Ściślej mówiąc, Edytuj i Kontynuuj nie obsługuje następujące zmiany:  
  
-   Dodawanie lub usuwanie deklaracji zewnętrznych.  
  
-   Zmiana podpisu lub organizowanie atrybuty deklaracji zewnętrznych.  
  
###  <a name="BKMK_ImportsEdits"></a> Import zmian  
 Edytuj i Kontynuuj nie zezwala na dodawanie, zmienianie lub usuwanie `Imports` instrukcji w trybie przerwania.  
  
###  <a name="BKMK_InterfaceDefinitionEdits"></a> Zmiany definicji interfejsu  
 Chociaż często możesz wprowadzić zmiany do elementów członkowskich, które implementują interfejsy, zmiany definicji interfejsu rzeczywiste zwykle nie są dozwolone przez Edytuj i Kontynuuj. Ściślej mówiąc, Edytuj i Kontynuuj nie obsługuje następujące zmiany:  
  
-   Dodawanie, zmienianie lub usuwanie członków interfejsu.  
  
-   Usuwanie istniejącego interfejsu.  
  
-   Zmiana modyfikator dostępu interfejsu.  
  
-   Zmiana hierarchii dziedziczenia interfejsu.  
  
###  <a name="BKMK_ModuleDeclarationEdits"></a> Edycje deklaracja modułu  
 Większość zmian deklaracje modułów nie są dozwolone przez Edytuj i Kontynuuj w trybie przerwania. Ściślej mówiąc, Edytuj i Kontynuuj nie obsługuje następujące zmiany:  
  
-   Tworzenie nowego modułu.  
  
-   Zmiana nazwy lub usuwanie istniejącego modułu.  
  
-   Zmiana modyfikator dostępu dla modułu.  
  
###  <a name="BKMK_ModuleMemberDeclarationEdits"></a> Edycje deklaracji elementu członkowskiego modułu  
 Za pomocą Edytuj i Kontynuuj, możesz wprowadzić szereg zmian członków modułu, takie jak właściwości, metod i pól w trybie przerwania. Niektóre zmiany, jednak nie są obsługiwane. W szczególności Edytuj i Kontynuuj nie obsługuje dodawanie, usuwanie lub zmiana typu lub podpis żadnych elementów członkowskich.  
  
 Ściślej mówiąc, Edytuj i Kontynuuj nie obsługuje następujące zmiany:  
  
-   Dodawanie nowego elementu członkowskiego, jeśli nie istnieją żadne wystąpienia o nazwie w żadnej aktywnej instrukcji.  
  
-   Usuwanie właściwości lub metody.  
  
-   Zmienianie podpisu właściwości lub metody.  
  
-   Dodawanie, zmienianie nazwy, przenoszenia lub usunięcie pola.  
  
-   Edytowanie dowolną metodę, która używa typów ogólnych.  
  
-   Zmiana modyfikatory dostępu do właściwości lub metody, na przykład zmiana `Public` do `Private`.  
  
-   Usuwanie lub zmiana typu istniejącego pola.  
  
###  <a name="BKMK_NestedTypeDeclarationEdits"></a> Edycje deklaracji typu zagnieżdżonego  
 Edytuj i Kontynuuj nie obsługuje przenoszenie typ zagnieżdżony do innej przestrzeni nazw lub typu.  
  
###  <a name="BKMK_StructureDeclarationEdits"></a> Edycje deklaracji struktury  
 Większość zmian wprowadzonych do deklaracji struktury nie są dozwolone przez Edytuj i Kontynuuj podczas w **Przerwij** trybu. Ściślej mówiąc, Edytuj i Kontynuuj nie obsługuje następujące zmiany:  
  
-   Zmiana nazwy lub usunięcie istniejącej struktury.  
  
-   Implementowanie nowy interfejs lub usuwanie implementacji interfejsu.  
  
-   Zmiana modyfikator dostępu dla struktury.  
  
###  <a name="BKMK_StructureMemberDeclarationEdits"></a> Edycje deklaracji elementu członkowskiego struktury  
 Za pomocą Edytuj i Kontynuuj, możesz wprowadzić szereg zmian elementy członkowskie struktury (właściwości, metod i pól) podczas w trybie przerwania. Niektóre zmiany, jednak nie są obsługiwane, zwłaszcza w przypadku zmiany, które wpływają na deklarację elementy członkowskie struktury. Ściślej mówiąc, Edytuj i Kontynuuj nie obsługuje następujące zmiany:  
  
-   Usuwanie właściwości lub metody.  
  
-   Dodawanie lub usuwanie pola.  
  
-   Zmienianie podpisu właściwości lub metody.  
  
-   Edytowanie dowolną metodę, która używa typów ogólnych.  
  
-   Zmiana, czy deklaracja właściwość lub metoda implementuje interfejs.  
  
-   Zmiana modyfikatory dostępu właściwości lub metody (na przykład zmiana `Public` do **prywatnej**).  
  
-   Usunięcie pola.  
  
-   Zmiana typu pola.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: stosowanie edycji w trybie przerwania za pomocą Edytuj i Kontynuuj](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [Edytuj i kontynuuj (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)



