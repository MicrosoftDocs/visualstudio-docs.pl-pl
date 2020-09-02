---
title: Ostrzeżenia VSInstr | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b178afb59558f5e684d704137039891aefbf0e3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683245"
---
# <a name="vsinstr-warnings"></a>Ostrzeżenia VSInstr
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniższa tabela zawiera listę ostrzeżeń wydawanych przez narzędzie VSInstr.exe. Można użyć opcji nowarn wraz z numerami ostrzegawczymi, aby pominąć wyświetlane ostrzeżenie.  
  
|Numer ostrzeżenia|Opis|  
|--------------------|-----------------|  
|**VSP2000**|Błąd wewnętrzny. Nie można pobrać nazwy pliku modułu dla tego pliku wykonywalnego.|  
|**VSP2001**|\<assembly name> jest zestawem o silnej nazwie. Aby można było wykonać te zmiany, należy je wcześniej podpisać.<br /><br /> To ostrzeżenie występuje, gdy podpisany zestaw jest Instrumentacją. Możesz użyć narzędzia sn.exe, aby zrezygnować z pliku binarnego lub tymczasowo wyłączyć wymaganie silnej nazwy. Aby uzyskać więcej informacji, zobacz [Sn.exe (Narzędzie silnej nazwy)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).|  
|**VSP2002**|Nie można znaleźć funkcji \<funcname> w pliku \<filename><br /><br /> To ostrzeżenie występuje, jeśli nie można zlokalizować funkcji w określonym pliku.|  
|**VSP2003**|Nie można znaleźć żadnych przeskoków krzyżowych do funkcji \<funcname> w pliku \<filename> .<br /><br /> To ostrzeżenie występuje, jeśli VSInstr nie zniesienia krzyżowe uskoków. Przeskoki krzyżowe są używane na potrzeby optymalizacji kodu.|  
|**VSP2004**|Funkcja \<funcname> została wykluczona przy użyciu przełącznika wiersza polecenia Exclude, ale jest wymagana, ponieważ zawierała krzyżyk przeskoku.<br /><br /> To ostrzeżenie występuje, jeśli funkcja została wykluczona przy użyciu opcji wykluczania, ale jest wymagana podczas procesu instrumentacji. Profiler automatycznie zawiera wymaganą funkcję.|  
|**VSP2005**|Wewnętrzny błąd Instrumentacji \<error text><br /><br /> To ostrzeżenie jest generowane, jeśli nie można wykonać Instrumentacji. Przejrzyj tekst błędu, aby ustalić, czy można go poprawić.|  
|**VSP2006**|Nie można znaleźć pliku PDB dla \<name><br /><br /> To ostrzeżenie występuje, jeśli plik PDB nie istnieje w ścieżce wyszukiwania lub nie jest zgodny z plikiem binarnym.|  
|**VSP2007**|\<filename> nie zawiera kodu Instrumentacji.<br /><br /> To ostrzeżenie jest generowane, jeśli wszystkie funkcje w pliku binarnym zostały wykluczone lub jeśli określony plik zawiera tylko zasoby.|  
|**VSP2008**|Nie można pobrać atrybutów zabezpieczeń z \<name> . Kod błędu \<code><br /><br /> To ostrzeżenie występuje, jeśli użytkownik nie ma uprawnienia READ_DAC. Podczas procesu instrumentacji profiler próbuje zachować oryginalną listę DACL dla pliku binarnego. Ponieważ oryginalny plik binarny jest zastępowany nowym plikiem binarnym, lista DACL z oryginalnego pliku binarnego musi zostać skopiowana i zastosowana do nowego pliku binarnego. Może to zakończyć się niepowodzeniem, jeśli użytkownik nie ma READ_DAC dostępu do oryginalnego pliku binarnego.|  
|**VSP2009**|Nie można ustawić atrybutów zabezpieczeń na \<name> . Kod błędu \<error number><br /><br /> To ostrzeżenie występuje, jeśli użytkownik nie ma uprawnienia WRITE_DAC. Podczas procesu instrumentacji profiler próbuje zachować oryginalną listę DACL dla pliku binarnego. Ponieważ oryginalny plik binarny jest zastępowany nowym plikiem binarnym, lista DACL z oryginalnego pliku binarnego musi zostać skopiowana i zastosowana do nowego pliku binarnego. Może to zakończyć się niepowodzeniem, jeśli użytkownik nie ma WRITE_DAC dostępu do nowego pliku binarnego.|  
|**VSP2010**|Nie wybrano żadnych funkcji dla Instrumentacji ze względu na opcje dołączania/wykluczania|  
|**VSP2011**|Funcspec dołączania/wykluczania nie \<name> pasuje do żadnych funkcji|  
|**VSP2012**|Obraz nie zawiera żadnego kodu, który może być Instrumentacją dla pokrycia kodu.<br /><br /> Profiler nie ma Instrumentacji następującego typu kodu:<br /><br /> -Statyczne funkcje CRT<br />Metody zarządzane z atrybutem NonUserCodeAttribute<br />Metody zarządzane z atrybutem DebuggerHiddenAttribute<br />-MASM bloki<br /><br /> To ostrzeżenie jest generowane, jeśli po filtrowaniu nie ma pozostałego kodu.|  
|**VSP2013**|Instrumentacja tego obrazu wymaga uruchomienia go jako procesu 32-bitowego. Flagi nagłówka CLR zostały zaktualizowane w celu odzwierciedlenia tego.<br /><br /> Profiler modyfikuje plik binarny, dzięki czemu 64-bitowe systemy operacyjne mogą otworzyć proces 32-bitowy w emulatorze emulatora WOW64. W przypadku bibliotek (dll) może to się nie powieść, jeśli są ładowane w istniejącym procesie 64-bitowym. To ostrzeżenie powiadamia użytkownika o zależności.|  
|**VSP2014**|Utworzony obraz z instrumentacją wydaje się nieprawidłowy i może nie zostać uruchomiony.<br /><br /> Ten komunikat występuje, gdy końcowy zestaw Instrumentacji ma nieprawidłowy nagłówek PE.|  
  
## <a name="see-also"></a>Zobacz też  
 [VSInstr](../profiling/vsinstr.md)
