---
title: Wtyczki kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7c51efc30251a177e07b7acf3e4c62821cb9488
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745456"
---
# <a name="source-control-plug-ins"></a>Wtyczki kontroli źródła
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sekcja dokumentacji zestawu SDK wtyczki kontroli źródła, zawiera specyfikację pełny interfejs, umożliwiająca systemów kontroli źródła można zintegrować z usługą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Określa, składnia i semantyka różne typy danych i funkcje, które wtyczka do kontroli źródła musi implementować interfejsu z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE).  
  
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
  
 [Instrukcje: wyłączanie ostrzeżenia dotyczącego zgodności dla wtyczek kontroli źródła](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Zawiera opis sposobu wyłączania ostrzeżeń.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przykładowa wtyczka kontroli źródła](http://msdn.microsoft.com/en-us/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Zawiera przykładowy funkcji wtyczki kontroli źródła.  
  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 W tym artykule opisano procedury badania dotyczące wtyczki kontroli źródła.  
  
 [Tworzenie wtyczki kontroli kodu źródłowego](../extensibility/internals/creating-a-source-control-plug-in.md)  
 W tym artykule omówiono sposób tworzenia wtyczki kontroli źródła dostarczającego funkcji kontroli źródła, gdy używasz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu użytkownika kontroli źródła (UI).  
  
 [Dokumentacja zestawu Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)  
 Wyświetla listę tematów odwołań.

