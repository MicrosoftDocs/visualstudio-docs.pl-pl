---
title: Ostrzeżenia VSInstr | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 079cf7681f8583b500068c0ca6aea60ce0fad66b
ms.sourcegitcommit: 5dc74b4fdff1357df43a19f6e8a51d7bf706abd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55767909"
---
# <a name="vsinstr-warnings"></a>Ostrzeżenia VSInstr
W poniższej tabeli wymieniono ostrzeżenia *VSInstr.exe* narzędzia. NOWARN — opcja wraz z numerów ostrzeżeń, które umożliwia Pomijaj wyświetlanie ostrzeżenia.  
  
|Numer ostrzeżenia|Opis|  
|--------------------|-----------------|  
|**VSP1026**|Pokrycie nie jest obsługiwane w bibliotekach, które nie odwołują się do elementu MSCorLib. Jest to często zdarza się w przypadku bibliotek przenośnych.<br /><br />[/Enablecodecoverage](/visualstudio/test/vstest-console-options) opcja wiersza polecenia jest wymagana dla platformy .NET Core.|  
|**VSP2000**|Błąd wewnętrzny. Nie można pobrać nazwy pliku modułu dla tego pliku wykonywalnego.|  
|**VSP2001**|\<Nazwa zestawu > jest zestaw o silnej nazwie. Musi zostać ponownie podpisany przed mogą być wykonywane.<br /><br /> To ostrzeżenie występuje, gdy został zinstrumentowany na zestawu podpisanego za pomocą. Możesz użyć *sn.exe* narzędzie ponownie podpisać plik binarny lub tymczasowo wyłączyć wymaganie silnej nazwy. Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnych nazw)](/dotnet/framework/tools/sn-exe-strong-name-tool).|  
|**VSP2002**|Nie można znaleźć funkcji \<funcname > w pliku \<nazwa pliku ><br /><br /> To ostrzeżenie występuje, jeśli funkcja nie może znajdować się w określonym pliku.|  
|**VSP2003**|Nie można znaleźć żadnych skrzyżowanych skoków do funkcji \<funcname > w pliku \<nazwa_pliku >.<br /><br /> To ostrzeżenie występuje, jeśli narzędzie VSInstr nie może zniweczyć przechodzi między. Skrzyżowany skok są używane do optymalizacji kodu.|  
|**VSP2004**|Funkcja \<funcname > została wykluczona przy użyciu przełącznika wiersza polecenia wykluczenia, ale była wymagana, ponieważ zawiera skok.<br /><br /> To ostrzeżenie występuje, jeśli funkcja został wykluczony, korzystając z opcji wykluczenia, ale jest wymagany w procesie instrumentacji. Program profilujący automatycznie uwzględnia wymaganej funkcji.|  
|**VSP2005**|Wewnętrzny błąd Instrumentacji \<tekst błędu ><br /><br /> To ostrzeżenie zostanie wyświetlone, jeśli nie można przeprowadzić instrumentacji. Przejrzyj tekst błędu, aby ustalić, czy mogą zostać poprawione.|  
|**VSP2006**|Nie można zlokalizować pliku PDB dla \<name ><br /><br /> To ostrzeżenie występuje, jeśli plik PDB nie istnieje w ścieżce wyszukiwania lub jest niezgodna z pliku binarnego.|  
|**VSP2007**|\<Nazwa pliku > nie zawiera kodu instrumentacji.<br /><br /> To ostrzeżenie zostanie wyświetlone, jeśli funkcje w pliku binarnym wszystkie wykluczone lub określony plik zawiera tylko zasoby.|  
|**VSP2008**|Nie można pobrać atrybutów zabezpieczeń z \<name >. Kod błędu: \<kod ><br /><br /> To ostrzeżenie występuje, jeśli użytkownik nie ma uprawnień READ_DAC. Podczas procesu Instrumentacji profilera próbuje zachować oryginalne DACL dla pliku binarnego. Ponieważ oryginalny plik binarny jest zastępowany odciskiem nowego pliku binarnego, DACL z oryginalny plik binarny należy skopiować i zastosowane do nowego pliku binarnego. Może zakończyć się niepowodzeniem, jeśli użytkownik nie ma dostępu READ_DAC na oryginalny plik binarny.|  
|**VSP2009**|Nie można ustawić atrybutów zabezpieczeń \<name >. Kod błędu: \<numer błędu ><br /><br /> To ostrzeżenie występuje, jeśli użytkownik nie ma uprawnień WRITE_DAC. Podczas procesu Instrumentacji profilera próbuje zachować oryginalne DACL dla pliku binarnego. Ponieważ oryginalny plik binarny jest zastępowany odciskiem nowego pliku binarnego, DACL z oryginalny plik binarny należy skopiować i zastosowane do nowego pliku binarnego. Może zakończyć się niepowodzeniem, jeśli użytkownik nie ma dostępu WRITE_DAC na nowe dane binarne.|  
|**VSP2010**|Żadne funkcje nie są specjalnie wybranych do Instrumentacji z powodu — OBEJMUJĄ opcje/WYKLUCZANIA|  
|**VSP2011**|Uwzględnianie/wykluczanie funcspec \<name > jest niezgodny z dowolnej funkcji|  
|**VSP2012**|Obraz, który nie zawiera kodu, który może być instrumentacji dla pokrycia kodu.<br /><br /> Profiler nie Instrumentacja następującego typu kodu:<br /><br /> — Statyczne funkcje CRT<br />-Zarządzanych metod z NonUserCodeAttribute<br />-Zarządzanych metod z DebuggerHiddenAttribute<br />-Bloki MASM<br /><br /> To ostrzeżenie jest generowany, jeśli po powyższym filtrowaniu nie ma kodu po lewej.|  
|**VSP2013**|Zinstrumentowanie tego obrazu wymagają, aby był uruchamiany jako proces 32-bitowy. Flagi nagłówka CLR zostały zaktualizowane w celu przedstawienia tej.<br /><br /> Program profilujący modyfikuje plik binarny, tak, aby otworzyć 32-bitowy proces 64-bitowych systemach operacyjnych w emulatorze WOW64. Dla bibliotek (dll) to może się nie powieść, jeśli są one załadowane w istniejących procesów 64-bitowych. To ostrzeżenie powiadamia użytkownika zależności.|  
|**VSP2014**|Wynikowy zinstrumentowany obraz wygląda na nieprawidłowy i może nie działać.<br /><br /> Ten komunikat występuje, gdy ostateczny zestaw instrumentowanych ma nieprawidłowy nagłówek PE.|  
  
## <a name="see-also"></a>Zobacz także  
 [VSInstr](../profiling/vsinstr.md)