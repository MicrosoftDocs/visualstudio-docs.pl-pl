---
title: Wtyczki kontroli źródła | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f45ffeb57db79edd6305c3195a87012dc7de26b7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923643"
---
# <a name="source-control-plug-ins"></a>Wtyczki kontroli źródła
Sekcja dokumentacji zestawu SDK wtyczki kontroli źródła, zawiera specyfikację pełny interfejs, umożliwiająca systemów kontroli źródła można zintegrować z usługą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Określa, składnia i semantyka różne typy danych i funkcje, które wtyczka do kontroli źródła musi implementować interfejsu z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)  
 Wyświetla listę funkcji, które muszą zostać zaimplementowane przez wtyczka do kontroli źródła aby można było zgodne z interfejsem API wtyczki kontroli źródła.  
  
 [Funkcje wywołania zwrotnego implementowane przez środowisko IDE](../extensibility/callback-functions-implemented-by-the-ide.md)  
 W tym artykule opisano funkcje, które wtyczka do kontroli źródła używa do przekazania informacji do środowiska IDE, podczas gdy niektóre polecenia zostaną wykonane.  
  
 [Moduły wyliczające](../extensibility/enumerators.md)  
 Wyświetla listę typów danych modułu wyliczającego w interfejsie API wtyczki kontroli źródła wtyczka do kontroli źródła należy wiedzieć o.  
  
 [Flagi możliwości](../extensibility/capability-flags.md)  
 W tym artykule opisano `SCC_CAP_xxx` flagi wskazujące możliwości dostawcy.  
  
 [Flagi bitowe używane przez określone polecenia ](../extensibility/bitflags-used-by-specific-commands.md)  
 Wyświetla listę flag, które są przydatne w kontekście określonego polecenia.  
  
 [Kody błędów](../extensibility/error-codes.md)  
 Wyświetla listę wartości typowych błędów zwracanych przez funkcje jako `SCCTRN`.  
  
 [Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 W tym artykule opisano klucze na potrzeby uzyskiwania dostępu do rejestru, aby znaleźć wtyczka do kontroli źródła.  
  
 [Plik MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)  
 W tym artykule opisano pliku po stronie klienta, zawierająca informacje nieprzezroczysta dla środowiska IDE, ale używanego przez wtyczka do kontroli źródła, aby znaleźć rozwiązania lub projektu w kontroli wersji.  
  
 [Najlepsze rozwiązania dotyczące wdrażania wtyczki kontroli źródła](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Zawiera kolekcję ważne przypomnienia Technical Preview do zapamiętania, natomiast w przypadku implementowania interfejsu API wtyczki kontroli źródła.  
  
 [Ograniczenia długości ciągów](../extensibility/restrictions-on-string-lengths.md)  
 W tym artykule opisano ograniczenia w interfejsie API wtyczki kontroli źródła na długości ciągów używanych w różnych funkcji.  
  
 [Słownik](../extensibility/source-control-plug-in-glossary.md)  
 Udostępnia przydatne warunki i ich definicje dla odczytu w dokumentacji zestawu SDK wtyczki kontroli źródła.  
  
 [Instrukcje: Wyłączanie ostrzeżenia dotyczącego zgodności dla wtyczek kontroli kodu źródłowego](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Zawiera opis sposobu wyłączania ostrzeżeń.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przykładowa wtyczka kontroli źródła](https://www.microsoft.com/download/details.aspx?id=55984)  
 Zawiera przykładowy funkcji wtyczki kontroli źródła.  
  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 W tym artykule opisano procedury badania dotyczące wtyczki kontroli źródła.  
  
 [Tworzenie wtyczki kontroli kodu źródłowego](../extensibility/internals/creating-a-source-control-plug-in.md)  
 W tym artykule omówiono sposób tworzenia wtyczki kontroli źródła dostarczającego funkcji kontroli źródła, gdy używasz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika kontroli źródła (UI).  
  
 [Dokumentacja zestawu Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)  
 Wyświetla listę tematów odwołań.