---
title: Ostrzeżenia VSInstr | Microsoft Docs
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f1a0cba29caeda01de1154430af7a0d94bcfc2a5
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779951"
---
# <a name="vsinstr-warnings"></a>Ostrzeżenia VSInstr
Poniższa tabela zawiera listę ostrzeżeń wydawanych przez narzędzie *VSInstr. exe* . Można użyć opcji nowarn wraz z numerami ostrzegawczymi, aby pominąć wyświetlane ostrzeżenie.

|Numer ostrzeżenia|Opis|
|--------------------|-----------------|
|**VSP1026**|Pokrycie nie jest obsługiwane w bibliotekach, które nie odwołują się do biblioteki MSCorLib. Jest to często przypadek dla bibliotek przenośnych.<br /><br />Opcja wiersza polecenia [/EnableCodeCoverage](../test/vstest-console-options.md) jest wymagana dla platformy .NET Core.|
|**VSP2000**|Błąd wewnętrzny. Nie można pobrać nazwy pliku modułu dla tego pliku wykonywalnego.|
|**VSP2001**|Nazwa zestawu \<> jest zestawem o silnej nazwie. Aby można było wykonać te zmiany, należy je wcześniej podpisać.<br /><br /> To ostrzeżenie występuje, gdy podpisany zestaw jest Instrumentacją. Możesz użyć narzędzia *SN. exe* , aby zrezygnować z pliku binarnego lub tymczasowo wyłączyć wymaganie silnej nazwy. Aby uzyskać więcej informacji, zobacz [SN. exe (Narzędzie silnej nazwy)](/dotnet/framework/tools/sn-exe-strong-name-tool).|
|**VSP2002**|Nie można znaleźć funkcji \<FuncName > w pliku \<nazw ><br /><br /> To ostrzeżenie występuje, jeśli nie można zlokalizować funkcji w określonym pliku.|
|**VSP2003**|Nie można znaleźć żadnych przeskoków krzyżowych do funkcji \<FuncName > w > pliku \<nazw.<br /><br /> To ostrzeżenie występuje, jeśli VSInstr nie zniesienia krzyżowe uskoków. Przeskoki krzyżowe są używane na potrzeby optymalizacji kodu.|
|**VSP2004**|Funkcja \<FuncName > została wykluczona przy użyciu przełącznika wiersza polecenia EXCLUDE, ale była wymagana, ponieważ zawierała krzyżyk uskoku.<br /><br /> To ostrzeżenie występuje, jeśli funkcja została wykluczona przy użyciu opcji wykluczania, ale jest wymagana podczas procesu instrumentacji. Profiler automatycznie zawiera wymaganą funkcję.|
|**VSP2005**|Wewnętrzny błąd Instrumentacji \<tekstowym błędów ><br /><br /> To ostrzeżenie jest generowane, jeśli nie można wykonać Instrumentacji. Przejrzyj tekst błędu, aby ustalić, czy można go poprawić.|
|**VSP2006**|Nie można zlokalizować pliku PDB dla nazwy \<<br /><br /> To ostrzeżenie występuje, jeśli plik PDB nie istnieje w ścieżce wyszukiwania lub nie jest zgodny z plikiem binarnym.|
|**VSP2007**|\<filename > nie zawiera kodu Instrumentacji.<br /><br /> To ostrzeżenie jest generowane, jeśli wszystkie funkcje w pliku binarnym zostały wykluczone lub jeśli określony plik zawiera tylko zasoby.|
|**VSP2008**|Nie można pobrać atrybutów zabezpieczeń z nazwy \<>. Kod błędu \<kod ><br /><br /> To ostrzeżenie występuje, jeśli użytkownik nie ma uprawnienia READ_DAC. Podczas procesu instrumentacji profiler próbuje zachować oryginalną listę DACL dla pliku binarnego. Ponieważ oryginalny plik binarny jest zastępowany nowym plikiem binarnym, lista DACL z oryginalnego pliku binarnego musi zostać skopiowana i zastosowana do nowego pliku binarnego. Może to zakończyć się niepowodzeniem, jeśli użytkownik nie ma READ_DAC dostępu do oryginalnego pliku binarnego.|
|**VSP2009**|Nie można ustawić atrybutów zabezpieczeń na \<nazw >. Kod błędu \<numer błędu ><br /><br /> To ostrzeżenie występuje, jeśli użytkownik nie ma uprawnienia WRITE_DAC. Podczas procesu instrumentacji profiler próbuje zachować oryginalną listę DACL dla pliku binarnego. Ponieważ oryginalny plik binarny jest zastępowany nowym plikiem binarnym, lista DACL z oryginalnego pliku binarnego musi zostać skopiowana i zastosowana do nowego pliku binarnego. Może to zakończyć się niepowodzeniem, jeśli użytkownik nie ma WRITE_DAC dostępu do nowego pliku binarnego.|
|**VSP2010**|Nie wybrano żadnych funkcji dla Instrumentacji ze względu na opcje dołączania/wykluczania|
|**VSP2011**|Nazwa dołączania/wykluczania funcspec \<> nie jest zgodna z żadną z funkcji|
|**VSP2012**|Obraz nie zawiera żadnego kodu, który może być Instrumentacją dla pokrycia kodu.<br /><br /> Profiler nie ma Instrumentacji następującego typu kodu:<br /><br /> -Statyczne funkcje CRT<br />Metody zarządzane z atrybutem NonUserCodeAttribute<br />Metody zarządzane z atrybutem DebuggerHiddenAttribute<br />-MASM bloki<br /><br /> To ostrzeżenie jest generowane, jeśli po filtrowaniu nie ma pozostałego kodu.|
|**VSP2013**|Instrumentacja tego obrazu wymaga uruchomienia go jako procesu 32-bitowego. Flagi nagłówka CLR zostały zaktualizowane w celu odzwierciedlenia tego.<br /><br /> Profiler modyfikuje plik binarny, dzięki czemu 64-bitowe systemy operacyjne mogą otworzyć proces 32-bitowy w emulatorze emulatora WOW64. W przypadku bibliotek (dll) może to się nie powieść, jeśli są ładowane w istniejącym procesie 64-bitowym. To ostrzeżenie powiadamia użytkownika o zależności.|
|**VSP2014**|Utworzony obraz z instrumentacją wydaje się nieprawidłowy i może nie zostać uruchomiony.<br /><br /> Ten komunikat występuje, gdy końcowy zestaw Instrumentacji ma nieprawidłowy nagłówek PE.|

## <a name="see-also"></a>Zobacz także
- [VSInstr](../profiling/vsinstr.md)
