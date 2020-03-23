---
title: Ostrzeżenia VSInstr | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779951"
---
# <a name="vsinstr-warnings"></a>Ostrzeżenia VSInstr
W poniższej tabeli wymieniono ostrzeżenia wydane przez narzędzie *VSInstr.exe.* Można użyć opcji NOWARN wraz z numerami ostrzegawczymi, aby pominąć wyświetlane ostrzeżenie.

|Numer ostrzeżenia|Opis|
|--------------------|-----------------|
|**VSP1026**|Pokrycie nie jest obsługiwane w bibliotekach, które nie odwołują się do usługi MSCorLib. Jest to często w przypadku bibliotek przenośnych.<br /><br />Opcja wiersza polecenia [/EnableCodeCoverage](../test/vstest-console-options.md) jest wymagana dla platformy .NET Core.|
|**VSP2000**|Błąd wewnętrzny. Nie można uzyskać nazwy pliku modułu dla tego pliku wykonywalnego.|
|**VSP2001**|\<nazwa zestawu> jest zestawem o silnie nazwanym nazwie. Musi być ponownie podpisany, zanim będzie można wykonać.<br /><br /> To ostrzeżenie występuje, gdy podpisany zestaw jest instrumentowany. Za pomocą narzędzia *sn.exe* można zrezygnować z pliku binarnego lub tymczasowo wyłączyć wymóg dotyczący silnej nazwy. Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnej nazwy)](/dotnet/framework/tools/sn-exe-strong-name-tool).|
|**VSP2002**|Nie można \<znaleźć funkcji funcname \<> w pliku><br /><br /> To ostrzeżenie występuje, jeśli funkcja nie może znajdować się w określonym pliku.|
|**VSP2003**|Nie można znaleźć żadnych przeskakuje krzyż do funkcji \<funcname> w pliku \<>.<br /><br /> To ostrzeżenie występuje, jeśli VSInstr nie może unieważnić przeskoków krzyżowych. Przeskoki krzyżowe są używane do optymalizacji kodu.|
|**VSP2004**|Funkcja \<funcname> została wykluczona za pomocą przełącznika wiersza polecenia EXCLUDE, ale była wymagana, ponieważ zawierała skok krzyżowy.<br /><br /> To ostrzeżenie występuje, jeśli funkcja została wykluczona za pomocą opcji WYKLUCZ, ale jest potrzebna podczas procesu instrumentacji. Profiler automatycznie zawiera wymaganą funkcję.|
|**VSP2005**|Tekst błędu \<o błędzie instrumentacji wewnętrznej><br /><br /> To ostrzeżenie jest wydawane, jeśli nie można wykonać oprzyrządowania. Przejrzyj tekst błędu, aby ustalić, czy można go poprawić.|
|**VSP2006**|Nie można zlokalizować \<bazy danych PDB dla> nazw<br /><br /> To ostrzeżenie występuje, jeśli plik PDB nie istnieje na ścieżce wyszukiwania lub nie pasuje do pliku binarnego.|
|**VSP2007**|\<nazwa pliku> nie zawiera kodu instrumentowa.<br /><br /> To ostrzeżenie jest wydawane, jeśli wszystkie funkcje w pliku binarnym zostały wykluczone lub określony plik zawiera tylko zasoby.|
|**VSP2008**|Nie można uzyskać \<atrybutów zabezpieczeń od> nazwy. Kod \<kodu błędu><br /><br /> To ostrzeżenie występuje, jeśli użytkownik nie ma READ_DAC uprawnień. Podczas procesu instrumentacji profiler próbuje zachować oryginalny DACL dla pliku binarnego. Ponieważ oryginalny plik binarny jest zastępowany nowym binarnym, list DACL z oryginalnego pliku binarnego musi zostać skopiowana i zastosowana do nowego pliku binarnego. Może to zakończyć się niepowodzeniem, jeśli użytkownik nie ma dostępu READ_DAC w oryginalnym pliku binarnym.|
|**VSP2009**|Nie można ustawić \<atrybutów zabezpieczeń na> nazwy. Numer \<błędu kodu><br /><br /> To ostrzeżenie występuje, jeśli użytkownik nie ma WRITE_DAC uprawnień. Podczas procesu instrumentacji profiler próbuje zachować oryginalny DACL dla pliku binarnego. Ponieważ oryginalny plik binarny jest zastępowany nowym binarnym, list DACL z oryginalnego pliku binarnego musi zostać skopiowana i zastosowana do nowego pliku binarnego. Może to zakończyć się niepowodzeniem, jeśli użytkownik nie ma dostępu WRITE_DAC na nowy plik binarny.|
|**VSP2010**|Żadne funkcje nie są specjalnie wybrane dla oprzyrządowania ze względu na opcje -INCLUDE/-EXCLUDE|
|**VSP2011**|Uwzględnij/Wyklucz nazwę \<funcspec> nie pasuje do żadnych funkcji|
|**VSP2012**|Obraz nie zawiera żadnego kodu, który może być instrumentowane dla pokrycia kodu.<br /><br /> Profiler nie instruuje następującego typu kodu:<br /><br /> - Statyczne funkcje CRT<br />- Metody zarządzane przypisane z nonusercodeattribute<br />- Zarządzane metody przypisane z DebuggerHiddenAttribute<br />- Bloki MASM<br /><br /> To ostrzeżenie jest generowane, jeśli po tym filtrowaniu nie ma kodu.|
|**VSP2013**|Instrumentowanie tego obrazu wymaga jego uruchomienia jako procesu 32-bitowego. Flagi nagłówka CLR zostały zaktualizowane, aby to odzwierciedlić.<br /><br /> Profiler modyfikuje binarne tak, że 64-bitowe systemy operacyjne mogą otworzyć proces 32-bitowy w emulatorze WOW64. W przypadku bibliotek (bibliotek DLL) może się to nie powieść, jeśli zostaną załadowane w istniejącym procesie 64-bitowym. To ostrzeżenie powiadamia użytkownika zależności.|
|**VSP2014**|Wynikowy obraz instrumentowany wydaje się być nieprawidłowy i może nie zostać uruchomiony.<br /><br /> Ten komunikat występuje, gdy końcowy instrumentowany zestaw ma nieprawidłowy nagłówek PE.|

## <a name="see-also"></a>Zobacz też
- [VSInstr](../profiling/vsinstr.md)
