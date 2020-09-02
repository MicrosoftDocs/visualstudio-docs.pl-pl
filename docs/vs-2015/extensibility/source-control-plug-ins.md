---
title: Wtyczki kontroli źródła | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5a99ebdf2366ce6a60a6a724afc7d742db7150f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705800"
---
# <a name="source-control-plug-ins"></a>Wtyczki kontroli źródła
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sekcja Dokumentacja zestawu SDK wtyczki kontroli źródła zawiera kompletną specyfikację interfejsu, która umożliwia zintegrowane systemy kontroli źródła [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Określa składnię i semantykę różnych funkcji i typów danych, które Wtyczka kontroli źródła musi zaimplementować do interfejsu za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)  
 Wyświetla listę funkcji, które muszą zostać zaimplementowane przez wtyczkę kontroli źródła w celu zapewnienia zgodności z interfejsem API kontroli źródła.  
  
 [Funkcje wywołania zwrotnego implementowane przez środowisko IDE](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Opisuje funkcje używane przez wtyczkę kontroli źródła do przekazywania informacji z powrotem do środowiska IDE podczas wykonywania niektórych poleceń.  
  
 [Modułów wyliczających](../extensibility/enumerators.md)  
 Wyświetla listę typów danych modułu wyliczającego w interfejsie API dodatku plug-in kontroli źródła, który musi znać Wtyczka kontroli źródła.  
  
 [Flagi możliwości](../extensibility/capability-flags.md)  
 Opisuje `SCC_CAP_xxx` flagi wskazujące możliwości dostawcy.  
  
 [Flagi bitowe używane przez określone polecenia ](../extensibility/bitflags-used-by-specific-commands.md)  
 Wyświetla listę flag, które są przydatne w kontekście konkretnych poleceń.  
  
 [Kody błędów](../extensibility/error-codes.md)  
 Wyświetla listę typowych wartości błędów zwracanych przez funkcje jako `SCCTRN` .  
  
 [Ciągi używane jako klucze do znajdowania wtyczki kontroli źródła](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Opisuje klucze służące do uzyskiwania dostępu do rejestru w celu znalezienia wtyczki kontroli źródła.  
  
 [Plik MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)  
 Opisuje plik po stronie klienta, który zawiera informacje nieprzezroczyste dla IDE, ale jest używany przez wtyczkę kontroli źródła do lokalizowania rozwiązania lub projektu w kontroli wersji.  
  
 [Najlepsze rozwiązania dotyczące wdrażania wtyczki kontroli źródła](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Zawiera kolekcję ważnych przypomnień technicznych, które należy zapamiętać podczas wdrażania interfejsu API wtyczki kontroli źródła.  
  
 [Ograniczenia długości ciągów](../extensibility/restrictions-on-string-lengths.md)  
 Opisuje ograniczenia w interfejsie API dodatku plug-in kontroli źródła dla długości ciągów używanych w różnych funkcjach.  
  
 [Słownik](../extensibility/source-control-plug-in-glossary.md)  
 Zawiera przydatne warunki i ich definicje umożliwiające odczytywanie dokumentacji zestawu SDK dodatku do kontroli źródła.  
  
 [Instrukcje: wyłączanie ostrzeżenia dotyczącego zgodności dla wtyczek kontroli źródła](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Opisuje sposób wyłączania ostrzeżeń.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przykład wtyczki kontroli źródła](https://msdn.microsoft.com/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Zapewnia przykład funkcji wtyczki kontroli źródła.  
  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Opisuje procedury testowania związane z wtyczką kontroli źródła.  
  
 [Tworzenie wtyczki kontroli kodu źródłowego](../extensibility/internals/creating-a-source-control-plug-in.md)  
 W tym artykule omówiono sposób tworzenia wtyczki kontroli źródła, która udostępnia funkcje kontroli źródła podczas korzystania z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu użytkownika kontroli źródła.  
  
 [Dokumentacja zestawu Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)  
 Przedstawia listę tematów referencyjnych.
