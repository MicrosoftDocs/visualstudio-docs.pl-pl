---
title: Nieobsługiwane edycje w Visual Basic Edytuj i Kontynuuj | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 94a151a7adab5c8246cec38c2e62d76788beb6e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155434"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Nieobsługiwane edycje funkcji Edytuj i kontynuuj programu Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytuj i Kontynuuj, aby zatrzymać wykonywanie programu w trybie przerwania, wprowadzić zmiany w kodzie wykonywanym i wznowić wykonywanie programu przy użyciu nowo wprowadzonych zmian. Deklaratywne edycje kodu, które mają wpływ na strukturę publiczną klasy, są ogólnie zabronione, ale wiele zmian, które mogą być wprowadzane do metody, treści właściwości lub prywatnych deklaracji w klasie, są dozwolone.  
  
 Jeśli trzeba wprowadzić zmianę, która nie jest obsługiwana, należy zatrzymać debugowanie, wprowadzić zmiany i rozpocząć nową sesję debugowania.  
  
### <a name="method-and-property-body-edits"></a><a name="BKMK_MethodandPropertyBodyEdits"></a> Edycja metod i treści właściwości  
 **Nieobsługiwane zmiany statycznych zmiennych lokalnych**: Dodawanie lub aktualizowanie zmiennej lokalnej lub usuwanie statycznej zmiennej lokalnej, jeśli spowoduje to błąd kompilacji.  
  
 **Nieobsługiwane zmiany w typach ogólnych**: zmiany metody ogólnej sama lub treści metody ogólnej nie są obsługiwane. Utworzenie wystąpienia typu ogólnego lub wywołania istniejących metod ogólnych można dodać, usunąć lub zmienić.  
  
 **Inne nieobsługiwane zmiany**  
  
- Zmiana instrukcji wywołania metody, która znajduje się na stosie wywołań.  
  
- Dodawanie `Try...Catch` bloku, gdy wskaźnik instrukcji zostanie zakończony w `Catch` bloku lub `Finally` bloku.  
  
- Usuwanie `Try...Catch` bloku, gdy wskaźnik instrukcji znajduje się w `Catch` bloku lub `Finally` bloku.  
  
- Dodawanie `Using` bloku wokół bieżącego wskaźnika instrukcji.  
  
- Dodawanie `SynchLock` bloku wokół bieżącego wskaźnika instrukcji.  
  
### <a name="attribute-edits"></a><a name="BKMK_AttributeEdits"></a> Edycje atrybutów  
 Edytuj i Kontynuuj nie obsługuje modyfikowania atrybutów. W przeciwnym razie polecenie Edytuj i Kontynuuj nie obsługuje następujących zmian:  
  
- Definiowanie, edytowanie lub usuwanie klasy atrybutów.  
  
- Dodawanie atrybutu.  
  
- Edytowanie lub usuwanie istniejącego atrybutu.  
  
### <a name="class-declaration-edits"></a><a name="BKMK_ClassDeclarationEdits"></a> Edycje deklaracji klasy  
 Większość zmian deklaracji klasy nie jest dozwolona przez edytowanie i kontynuowanie w trybie przerwania. W przeciwnym razie polecenie Edytuj i Kontynuuj nie obsługuje następujących zmian:  
  
- Zmiana nazwy, usunięcie lub zmiana dziedziczenia istniejącej klasy.  
  
- Implementowanie nowego interfejsu lub usuwanie implementacji interfejsu.  
  
- Zmienianie modyfikatorów w klasie.  
  
- Dodawanie, zmienianie lub usuwanie `ComClass` stanu.  
  
- Edytowanie dowolnej ogólnej deklaracji klasy.  
  
### <a name="class-member-declaration-edits"></a><a name="BKMK_ClassMemberDeclarationEdits"></a> Edytowanie deklaracji składowej klasy  
 Zmiany w deklaracjach składowych są zabronione w większości przypadków Edytuj i Kontynuuj. Na przykład nie można zmienić poziomu podpisu ani dostępu elementu członkowskiego i nie można całkowicie usunąć członków, jeśli spowodowałoby to błąd kompilacji. W przeciwnym razie polecenie Edytuj i Kontynuuj nie obsługuje następujących zmian:  
  
- Obserwowanie istniejącej zmiennej składowej przez zadeklarowanie globalnej lub zmiennej składowej o tej samej nazwie w bloku zawierającym.  
  
- Obserwowanie statycznej zmiennej lokalnej przez zadeklarowanie nowego wystąpienia wewnątrz bloku.  
  
- Usuwanie programów obsługi dla zdarzenia. Dodawanie programu obsługi zdarzeń jest dozwolone.  
  
- Dodawanie nowej właściwości lub metody przeciążania, chyba że właściwość lub metoda ma `Private` i nie ma wystąpień nazwy w żadnej aktywnej instrukcji.  
  
- Dodawanie lub usuwanie `WithEvents` klauzuli w zmiennej składowej.  
  
- Usuwanie elementu członkowskiego.  
  
- Zmiana właściwości lub deklaracji metody, aby zatrzymać implementację interfejsu.  
  
- Edytowanie dowolnej metody, która używa typów ogólnych.  
  
- Zmiana sygnatury lub zwracanego typu nieprywatnej właściwości lub metody.  
  
- Zastępowanie lub obserwowanie elementu członkowskiego w klasie bazowej.  
  
- Dodawanie nowego pola w dowolnej klasie oznaczonej przy użyciu `SequentialLayout` lub `ExplicitLayout` .  
  
- Zmiana `MustInherit` stanu lub `NotOverridable` metody.  
  
- Zmiana modyfikatorów dostępu dla właściwości lub metody.  
  
- Zmiana typu lub stanu tylko do odczytu pola.  
  
- Zmiana pola publicznego.  
  
### <a name="compiler-option-edits"></a><a name="BKMK_CompilerOptionEdits"></a> Edycja opcji kompilatora  
 Korzystając z funkcji Edytuj i Kontynuuj w trybie przerwania, nie można zmieniać, dodawać ani usuwać następujących opcji kompilatora:  
  
- **Option Strict**  
  
- **Opcja Explicit**  
  
- **Opcja Porównaj**  
  
### <a name="constants-edits"></a><a name="BKMK_ConstantsEdits"></a> Stałe modyfikacje  
 Zmiany w stałych w trybie Edytuj i Kontynuuj są bardzo ograniczone. W przeciwnym razie polecenie Edytuj i Kontynuuj nie obsługuje następujących zmian:  
  
- Dodawanie lub aktualizowanie zmiennej stałej.  
  
- Zmiana typu lub wartości stałej.  
  
- Usuwanie stałej.  
  
### <a name="delegate-and-event-declaration-edits"></a><a name="BKMK_DelegateandEventDeclarationEdits"></a> Operacje delegowania i deklaracji zdarzeń  
 Niektóre zmiany delegatów i zdarzeń nie są dozwolone przez edytowanie i kontynuowanie w trybie przerwania. W przeciwnym razie polecenie Edytuj i Kontynuuj nie obsługuje następujących zmian:  
  
- Zmienianie lub usuwanie definicji delegata.  
  
- Usuwanie zdarzenia.  
  
### <a name="enumeration-edits"></a><a name="BKMK_EnumerationEdits"></a> Edycje wyliczenia  
 Zmiany w wyliczeniach ( `Enums` ) nie są dozwolone przez edytowanie i kontynuowanie w trybie przerwania. W przeciwnym razie polecenie Edytuj i Kontynuuj nie obsługuje następujących zmian:  
  
- Modyfikowanie typu podstawowego `Enum` .  
  
- Dodawanie, zmienianie lub usuwanie `Enum` elementu członkowskiego.  
  
- Zmiana modyfikatora dostępu `Enum` .  
  
### <a name="external-declarations-edits"></a><a name="BKMK_ExternalDeclarationsEdits"></a> Edycje deklaracji zewnętrznych  
 Ogólnie rzecz biorąc nie można zmienić deklaracji metod zewnętrznych podczas Edytuj i Kontynuuj. W przeciwnym razie polecenie Edytuj i Kontynuuj nie obsługuje następujących zmian:  
  
- Dodawanie lub usuwanie deklaracji zewnętrznej.  
  
- Zmienianie podpisu lub organizowanie atrybutów zewnętrznej deklaracji.  
  
### <a name="imports-edits"></a><a name="BKMK_ImportsEdits"></a> Importuje edycje  
 Polecenie Edytuj i Kontynuuj nie umożliwia dodawania, zmieniania ani usuwania `Imports` instrukcji w trybie przerwania.  
  
### <a name="interface-definition-edits"></a><a name="BKMK_InterfaceDefinitionEdits"></a> Edytowanie definicji interfejsu  
 Chociaż często można wprowadzać zmiany do elementów członkowskich, które implementują interfejsy, zmiany w rzeczywistych definicjach interfejsów zazwyczaj nie są dozwolone przez polecenie Edytuj i Kontynuuj. W przeciwnym razie polecenie Edytuj i Kontynuuj nie obsługuje następujących zmian:  
  
- Dodawanie, zmienianie lub usuwanie elementów członkowskich interfejsu.  
  
- Usuwanie istniejącego interfejsu.  
  
- Zmiana modyfikatora dostępu interfejsu.  
  
- Zmiana hierarchii dziedziczenia interfejsu.  
  
### <a name="module-declaration-edits"></a><a name="BKMK_ModuleDeclarationEdits"></a> Edycje deklaracji modułu  
 Większość zmian deklaracji modułów nie jest dozwolona przez edytowanie i kontynuowanie w trybie przerwania. W przeciwnym razie polecenie Edytuj i Kontynuuj nie obsługuje następujących zmian:  
  
- Tworzenie nowego modułu.  
  
- Zmiana nazwy lub usunięcie istniejącego modułu.  
  
- Zmiana modyfikatora dostępu dla modułu.  
  
### <a name="module-member-declaration-edits"></a><a name="BKMK_ModuleMemberDeclarationEdits"></a> Edycja deklaracji elementu członkowskiego modułu  
 Za pomocą funkcji Edytuj i Kontynuuj można wprowadzać różne zmiany w elementach członkowskich modułu, takich jak właściwości, metody i pola, w trybie przerwania. Niektóre zmiany nie są jednak obsługiwane. W szczególności, polecenie Edytuj i Kontynuuj nie obsługuje dodawania, usuwania ani zmieniania typu lub podpisu żadnych elementów członkowskich.  
  
 W przeciwnym razie polecenie Edytuj i Kontynuuj nie obsługuje następujących zmian:  
  
- Dodawanie nowego elementu członkowskiego, jeśli nie ma żadnych wystąpień nazwy w żadnej aktywnej instrukcji.  
  
- Usuwanie właściwości lub metody.  
  
- Zmiana sygnatury właściwości lub metody.  
  
- Dodawanie, zmiana nazwy, przechodzenie lub usuwanie pola.  
  
- Edytowanie dowolnej metody, która używa typów ogólnych.  
  
- Zmiana modyfikatorów dostępu dla właściwości lub metody, na przykład zmiana `Public` na `Private` .  
  
- Usuwanie lub zmiana typu istniejącego pola.  
  
### <a name="nested-type-declaration-edits"></a><a name="BKMK_NestedTypeDeclarationEdits"></a> Edycje deklaracji typu zagnieżdżonego  
 Edytuj i Kontynuuj nie obsługuje przeniesienia typu zagnieżdżonego do innej przestrzeni nazw lub typu.  
  
### <a name="structure-declaration-edits"></a><a name="BKMK_StructureDeclarationEdits"></a> Edycje deklaracji struktury  
 Większość zmian w deklaracjach struktury nie jest dozwolona przez edytowanie i kontynuowanie w trybie **przerwania** . W przeciwnym razie polecenie Edytuj i Kontynuuj nie obsługuje następujących zmian:  
  
- Zmiana nazwy lub usunięcie istniejącej struktury.  
  
- Implementowanie nowego interfejsu lub usuwanie implementacji interfejsu.  
  
- Zmiana modyfikatora dostępu dla struktury.  
  
### <a name="structure-member-declaration-edits"></a><a name="BKMK_StructureMemberDeclarationEdits"></a> Edytowanie deklaracji składowej struktury  
 Za pomocą funkcji Edytuj i Kontynuuj można wprowadzać różne zmiany w elementach członkowskich struktury (właściwości, metody i pola) w trybie przerwania. Niektóre zmiany nie są jednak obsługiwane, w szczególności zmiany, które wpływają na deklarację elementów członkowskich struktury. W przeciwnym razie polecenie Edytuj i Kontynuuj nie obsługuje następujących zmian:  
  
- Usuwanie właściwości lub metody.  
  
- Dodawanie lub usuwanie pola.  
  
- Zmiana sygnatury właściwości lub metody.  
  
- Edytowanie dowolnej metody, która używa typów ogólnych.  
  
- Zmiana, czy Deklaracja właściwości lub metody implementuje interfejs.  
  
- Zmiana modyfikatorów dostępu właściwości lub metody (na przykład zmiana `Public` na **prywatną**).  
  
- Usuwanie pola.  
  
- Zmiana typu pola.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: stosowanie edycji w trybie przerwania za pomocą Edytuj i Kontynuuj](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [Edytuj i kontynuuj (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
