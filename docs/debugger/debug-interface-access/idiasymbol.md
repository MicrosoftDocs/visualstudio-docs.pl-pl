---
title: IDiaSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol interface
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0214d3e8d097efa31b3f8b02e67f419226a093a4
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461344"
---
# <a name="idiasymbol"></a>IDiaSymbol
Opisuje właściwości wystąpienia symbolu.

## <a name="syntax"></a>Składnia

```
IDiaSymbol : IUnknown
```

## <a name="methods-in-alphabetical-order"></a>Metody w kolejności alfabetycznej
W poniższej tabeli przedstawiono metody `IDiaSymbol` .

> [!NOTE]
> Symbole będą zwracać znaczące dane tylko dla niektórych z tych metod, w zależności od typu symbolu. Jeśli metoda zwróci metodę `S_OK` , ta metoda zwraca dane istotne.

|Metoda|Opis|
|------------|-----------------|
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|Pobiera wszystkie elementy podrzędne symbolu.|
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|Pobiera elementy podrzędne symbolu. Ta metoda jest rozszerzoną wersją [IDiaSymbol:: findChildren —](../../debugger/debug-interface-access/idiasymbol-findchildren.md).|
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|Pobiera elementy podrzędne symbolu, które są prawidłowe pod określonym adresem.|
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|Pobiera elementy podrzędne symbolu, które są prawidłowe w określonym względnym adresie wirtualnym (RVA).|
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|Pobiera elementy podrzędne symbolu, które są prawidłowe na określonym adresie wirtualnym.|
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|Pobiera wyliczenie, które pozwala klientowi na iterację we wszystkich wbudowanych ramkach na danym adresie.|
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|Pobiera wyliczenie, które pozwala klientowi na iterację we wszystkich wbudowanych ramkach w określonym względnym adresie wirtualnym (RVA).|
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|Pobiera wyliczenie, które pozwala klientowi na iterację we wszystkich wbudowanych ramkach w określonym adresie wirtualnym (VA).|
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, w tym symbolu.|
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, w tym symbolu w ramach określonego zakresu adresów.|
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, w tym symbolu w ramach określonego względnego adresu wirtualnego (RVA).|
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|Pobiera wyliczenie, które umożliwia klientowi przechodzenie do kolejnych informacji o numerze wiersza wszystkich funkcji, które są wbudowane, bezpośrednio lub pośrednio, w tym symbolu w określonym adresie wirtualnym (VA).|
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|Mając odpowiednią wartość tagu, ta metoda zwraca Wyliczenie symboli, które są zawarte w tej funkcji zastępczej w określonym względnym adresie wirtualnym.|
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|Zwraca liczbę tagów wskaźnika akceleratora w funkcji zastępczej C++ AMP.|
|[IDiaSymbol::get_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|Zwraca wszystkie wartości tagów wskaźnika akceleratora, które odpowiadają funkcji zastępczej akceleratora C++ AMP.|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|Pobiera modyfikator dostępu członka klasy.|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|Pobiera część przesunięcia lokalizacji adresu.|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|Pobiera część sekcji lokalizacji adresowej.|
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|Pobiera flagę wskazującą, czy inny symbol odwołuje się do tego adresu.|
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|Pobiera wartość wieku bazy danych programu.|
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|Pobiera identyfikator symbolu typu indeksu tablicy.|
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|Pobiera identyfikator typu indeksu tablicy symbolu.|
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|Pobiera główny numer wersji zaplecza.|
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|Pobiera pomocniczy numer wersji zaplecza.|
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|Pobiera numer kompilacji zaplecza.|
|[IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|Pobiera przesunięcie danych podstawowych.|
|[IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|Pobiera bazowe miejsce na dane.|
|[IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|Pobiera symbol, z którego bazuje wskaźnik.|
|[IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|Pobiera identyfikator symbolu, z którego bazuje wskaźnik.|
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|Pobiera tag typu prostego.|
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|Pobiera pozycję bitu lokalizacji.|
|[IDiaSymbol::get_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|Pobiera wbudowany rodzaj typu HLSL.|
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|Zwraca wskaźnik konwencji wywoływania metody.|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|Pobiera odwołanie do klasy nadrzędnej symbolu.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|Pobiera nadrzędny identyfikator klasy symbolu.|
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|Pobiera flagę wskazującą, czy symbol odwołuje się do adresu kodu.|
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|Pobiera flagę wskazującą, czy symbol został wygenerowany przez kompilator.|
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|Pobiera nazwę kompilatora użytego do utworzenia [jednostka kompilacji](../../debugger/debug-interface-access/compiland.md).|
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|Pobiera flagę wskazującą, czy typem danych zdefiniowanym przez użytkownika jest Konstruktor.|
|[IDiaSymbol::get_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|Pobiera zawierający symbol tego symbolu.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|Pobiera flagę wskazującą, czy typem danych zdefiniowanym przez użytkownika jest stała.|
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|Pobiera liczbę elementów z listy lub tablicy.|
|[IDiaSymbol::get_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|Pobiera liczbę prawidłowych zakresów adresów skojarzonych z symbolem lokalnym.|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|Pobiera flagę wskazującą, czy funkcja używa niestandardowej konwencji wywoływania.|
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|Pobiera bajty danych symbolu producenta OEM.|
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|Pobiera klasyfikację zmiennej symbolu danych.|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|Pobiera flagę opisującą funkcje Edytuj i Kontynuuj skompilowanego programu lub jednostki.|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|Pobiera flagę wskazującą, czy funkcja używa daleko Return.|
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|Pobiera numer wersji głównej frontonu.|
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|Pobiera numer wersji pomocniczej frontonu.|
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|Pobiera numer kompilacji frontonu.|
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|Pobiera flagę wskazującą, czy symbol publiczny odwołuje się do funkcji.|
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|Pobiera identyfikator GUID symbolu.|
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|Pobiera flagę wskazującą, czy funkcja zawiera wywołanie `alloca` .|
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika ma zdefiniowane wszystkie operatory przypisania.|
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika ma zdefiniowane wszystkie operatory rzutowania.|
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|Pobiera flagę wskazującą, czy jednostka kompilacji zawiera wszystkie informacje o debugowaniu.|
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|Pobiera flagę wskazującą, czy funkcja ma procedurę obsługi wyjątków w stylu języka C++.|
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|Pobiera flagę wskazującą, czy funkcja ma asynchroniczną procedurę obsługi wyjątków.|
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|Pobiera flagę wskazującą, czy funkcja ma wbudowany zestaw.|
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|Pobiera flagę wskazującą, czy funkcja zawiera polecenie longjmp (część obsługi wyjątków w stylu języka C).|
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|Pobiera flagę wskazującą, czy moduł zawiera kod zarządzany.|
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika ma definicje typów zagnieżdżonych.|
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|Pobiera flagę wskazującą, czy funkcja lub jednostka kompilacji mają skompilowane testy zabezpieczeń (za pośrednictwem przełącznika kompilatora [/GS (sprawdzanie zabezpieczeń bufora)](/cpp/build/reference/gs-buffer-security-check) .|
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|Pobiera flagę wskazującą, czy funkcja ma strukturalną obsługę wyjątków w stylu Win32.|
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|Pobiera flagę wskazującą, czy funkcja zawiera polecenie setjmp.|
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika jest pośrednią wirtualną klasą bazową.|
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|Pobiera flagę wskazującą, czy funkcja została oznaczona przy użyciu atrybutu wbudowanego.|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|Pobiera flagę wskazującą, czy funkcja ma zwrot z instrukcji przerwania.|
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|Pobiera flagę wskazującą, czy funkcja jest funkcją wirtualną klasy bazowej.|
|[IDiaSymbol::get_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|Pobiera flagę wskazującą, czy symbol odnosi się do udostępnionej zmiennej lokalnej grupy w kodzie skompilowanym dla akceleratora C++ AMP.|
|[IDiaSymbol::get_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|Pobiera flagę wskazującą, czy symbol odpowiada *symbolowi zakresu definicji* dla składnika znacznika zmiennej wskaźnika w kodzie skompilowanym dla akceleratora C++ amp. Symbol zakresu definicji jest lokalizacją zmiennej dla zakresu adresów.|
|[IDiaSymbol::get_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|Wskazuje, czy symbol odnosi się do symbolu funkcji najwyższego poziomu dla modułu cieniującego skompilowanego dla akceleratora, który odnosi się do `parallel_for_each` wywołania.|
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|Pobiera flagę wskazującą, czy dane są częścią agregacji wielu symboli.|
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|Pobiera flagę wskazującą, czy plik symboli zawiera typy C.|
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|Pobiera flagę wskazującą, czy moduł został przekonwertowany z wspólnego języka pośredniego (CIL) na kod natywny.|
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|Pobiera flagę wskazującą, czy elementy typu danych zdefiniowanego przez użytkownika są wyrównane do określonej granicy.|
|[IDiaSymbol::get_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|Określa, czy ten symbol reprezentuje dane języka cieniowania wysokiego poziomu (HLSL).|
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|Pobiera flagę wskazującą, czy moduł został skompilowany przy użyciu przełącznika kompilatora [/hotpatch (Create możliwy do poprawiania Image)](/cpp/build/reference/hotpatch-create-hotpatchable-image) .|
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|Pobiera flagę wskazującą, czy zarządzany jednostka kompilacji został połączony z LTCG konsolidatora.|
|[IDiaSymbol::get_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|Określa, czy macierz jest głównym wierszem.|
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|Pobiera flagę wskazującą, czy zarządzany jednostka kompilacji jest modułem. (zawierającym tylko metadane).|
|[IDiaSymbol::get_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|Określa, czy `this` wskaźnik wskazuje element członkowski danych z wielokrotnym dziedziczeniem.|
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|Pobiera flagę wskazującą, czy funkcja ma atrybut [owies](/cpp/cpp/naked-cpp) .|
|[IDiaSymbol::get_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|Określa, czy zmienna jest zoptymalizowana.|
|[IDiaSymbol::get_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|Określa, czy `this` wskaźnik jest oparty na wartości symbolicznej.|
|[IDiaSymbol::get_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|Określa, czy ten symbol jest wskaźnikiem do elementu członkowskiego danych.|
|[IDiaSymbol::get_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|Określa, czy ten symbol jest wskaźnikiem do funkcji składowej.|
|[IDiaSymbol::get_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|Określa, czy zmienna przenosi wartość zwracaną.|
|[IDiaSymbol::get_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|Określa, czy moduł jest kompilowany przy użyciu opcji/SDL.|
|[IDiaSymbol::get_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|Określa, czy `this` wskaźnik wskazuje element członkowski danych z pojedynczym dziedziczeniem.|
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|Pobiera flagę wskazującą, czy dane zostały podzielone na agregację oddzielnych symboli.|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|Pobiera flagę wskazującą, czy funkcja lub warstwa thunk są statyczne.|
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|Pobiera flagę wskazującą, czy symbole prywatne zostały usunięte z pliku symboli.|
|[IDiaSymbol::get_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|Określa, czy `this` wskaźnik wskazuje element członkowski danych z wirtualnym dziedziczeniem.|
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|Pobiera język źródła.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|Pobiera liczbę bajtów pamięci używanej przez obiekt reprezentowany przez ten symbol.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|Pobiera odwołanie do leksykalnego elementu nadrzędnego symbolu.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|Pobiera leksykalny nadrzędny identyfikator symbolu.|
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|Pobiera nazwę pliku biblioteki lub pliku obiektu, z którego został załadowany obiekt.|
|[IDiaSymbol::get_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|Zwraca długość zakresu adresów, w którym lokalny symbol jest prawidłowy.|
|[IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|Zwraca część sekcji zakresu adresów początkowych, w której lokalny symbol jest prawidłowy.|
|[IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|Zwraca część przesunięcia zakresu adresów początkowych, w której lokalny symbol jest prawidłowy.|
|[IDiaSymbol::get_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|Zwraca początek zakresu adresów, w którym lokalny symbol jest prawidłowy.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|Pobiera typ lokalizacji symbolu danych.|
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|Pobiera dolną granicę wymiaru tablicy Pascal.|
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|Pobiera identyfikator symbolu dolnej granicy wymiaru tablicy Pascal.|
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|Pobiera typ docelowego procesora CPU.|
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|Pobiera flagę wskazującą, czy symbol odwołuje się do kodu zarządzanego.|
|[IDiaSymbol::get_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|Pobiera Rodzaj przestrzeni pamięci.|
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|Pobiera flagę wskazującą, czy symbol odwołuje się do kodu języka pośredniego firmy Microsoft (MSIL).|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|Pobiera nazwę symbolu.|
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika jest zagnieżdżony.|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|Pobiera flagę wskazującą, czy funkcja jest oznaczona przy użyciu atrybutu [NoLine](/cpp/cpp/noinline) .|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|Pobiera flagę wskazującą, czy funkcja została zadeklarowana przy użyciu atrybutu [noreturn](/cpp/cpp/noreturn) .|
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|Pobiera flagę wskazującą, czy nie można wykonać porządkowania stosu w ramach sprawdzania buforu stosu.|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|Pobiera flagę wskazującą, czy funkcja lub etykieta nie są nigdy osiągalne.|
|[IDiaSymbol::get_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|Zwraca liczbę tagów wskaźnika akceleratora w funkcji zastępczej C++ AMP.|
|[IDiaSymbol::get_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|Pobiera liczbę modyfikatorów, które są stosowane do oryginalnego typu.|
|[IDiaSymbol::get_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|Pobiera liczbę indeksów rejestru.|
|[IDiaSymbol::get_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|Pobiera liczbę wierszy w macierzy.|
|[IDiaSymbol::get_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|Pobiera liczbę kolumn w macierzy.|
|[IDiaSymbol::get_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|Pobiera nazwę pliku obiektu.|
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|Pobiera typ wskaźnika obiektu dla metody klasy.|
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|Pobiera `oemId` wartość symbolu.|
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|Pobiera `oemSymbolId` wartość symbolu.|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|Pobiera przesunięcie lokalizacji symboli.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|Pobiera flagę wskazującą, czy funkcja lub etykieta zawiera zoptymalizowany kod oraz informacje o debugowaniu.|
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika ma przeciążone operatory.|
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika jest spakowany.|
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|Pobiera typ platformy, dla której został skompilowany program lub jednostka kompilacji.|
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|Pobiera flagę wskazującą, czy funkcja jest czystym elementem wirtualnym.|
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|Pobiera rangę tablicy wielowymiarowej Pascal.|
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|Pobiera flagę wskazującą, czy typ wskaźnika jest odwołaniem.|
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|Pobiera oznaczenie rejestru lokalizacji.|
|[IDiaSymbol::get_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|Pobiera typ rejestru.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|Pobiera względny adres wirtualny (RVA) lokalizacji.|
|[IDiaSymbol::get_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|Określa, czy `this` wskaźnik jest oflagowany jako ograniczony.|
|[IDiaSymbol::get_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|Pobiera gniazdo próbnika.|
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika pojawia się w nieglobalnym zakresie leksykalnym.|
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|Pobiera wartość podpisu symbolu.|
|[IDiaSymbol::get_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|Pobiera rozmiar elementu członkowskiego typu zdefiniowanego przez użytkownika.|
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|Pobiera numer gniazda lokalizacji.|
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|Pobiera nazwę pliku źródłowego.|
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|Pobiera plik źródłowy i numer wiersza wskazujący miejsce zdefiniowania określonego typu zdefiniowanego przez użytkownika.|
|[IDiaSymbol::get_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|Pobiera krok macierzy lub tablicy krokowej.|
|[IDiaSymbol::get_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|Pobiera podtyp.|
|[IDiaSymbol::get_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|Pobiera identyfikator podtypu.|
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|Pobiera nazwę pliku, z którego zostały załadowane symbole.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|Pobiera unikatowy identyfikator symbolu.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|Pobiera klasyfikator typu symbolu.|
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|Pobiera sekcję przesunięcia elementu docelowego thunk.|
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|Pobiera względny adres wirtualny (RVA) elementu docelowego thunk.|
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|Pobiera sekcję Address elementu docelowego thunk.|
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|Pobiera adres wirtualny (VA) elementu docelowego thunk.|
|[IDiaSymbol::get_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|Pobiera gniazdo tekstury.|
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|Pobiera logiczny `this` regulator dla metody.|
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|Pobiera typ thunk funkcji.|
|[IDiaSymbol::get_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|Pobiera sygnaturę czasową źródłowego pliku wykonywalnego.|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|Pobiera token metadanych zarządzanej funkcji lub zmiennej.|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|Pobiera odwołanie do sygnatury funkcji.|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|Pobiera identyfikator typu symbolu.|
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|Pobiera tablicę wartości typu specyficznego dla kompilatora dla tego symbolu.|
|[IDiaSymbol::get_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|Pobiera tablicę wartości identyfikatorów typu specyficznych dla kompilatora dla tego symbolu.|
|[IDiaSymbol::get_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Pobiera gniazdo UAV.|
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|Pobiera odmianę typu zdefiniowanego przez użytkownika (UDT).|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika nie jest wyrównany.|
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|Pobiera niedekoracyjną nazwę dla języka C++ (lub powiązania, nazwa).|
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|Rozszerzenie `get_undecoratedName` metody, która pobiera niedekoracyjną nazwę na podstawie wartości pola rozszerzenia.|
|[IDiaSymbol::get_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|Pobiera identyfikator oryginalnego (niezmodyfikowanego) typu.|
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|Pobiera górną granicę wymiaru tablicy Pascal.|
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|Pobiera identyfikator symbolu górnej granicy wymiaru tablicy Pascal.|
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|Pobiera wartość stałej.|
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|Pobiera flagę wskazującą, czy funkcja jest wirtualna.|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|Pobiera adres wirtualny (VA) lokalizacji.|
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika jest wirtualną klasą bazową.|
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|Pobiera indeks do tabeli przemieszczenia wirtualnego.|
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|Pobiera przesunięcie w tabeli funkcji wirtualnych funkcji wirtualnej.|
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|Pobiera przesunięcie wirtualnego wskaźnika bazowego.|
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|Pobiera typ wskaźnika wirtualnej tabeli bazowej.|
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|Pobiera interfejs symbol typu tabeli wirtualnej dla typu zdefiniowanego przez użytkownika.|
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|Pobiera identyfikator kształtu tabeli wirtualnej symbolu.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|Pobiera flagę wskazującą, czy typ danych zdefiniowany przez użytkownika jest nietrwały.|

## <a name="remarks"></a>Uwagi

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Uzyskaj ten interfejs, wywołując jedną z następujących metod:

- [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)

- [IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)

- [IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)

- [IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)

- [IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)

- [IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)

- [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)

- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)

- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)

- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)

- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)

- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)

- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)

- [IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)

- [IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)

- [IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)

## <a name="example"></a>Przykład
Ten przykład pokazuje, jak wyświetlić zmienne lokalne dla funkcji pod podanym względnym adresem wirtualnym. Pokazuje również, jak symbole różnych typów są ze sobą powiązane.

> [!NOTE]
> `CDiaBSTR`jest klasą, która zawija `BSTR` i automatycznie obsługuje zwalnianie ciągu, gdy utworzenie wystąpienia wykracza poza zakres.

```C++
void DumpLocalVars( DWORD rva, IDiaSession *pSession )
{
    CComPtr< IDiaSymbol > pBlock;
    if ( FAILED( psession->findSymbolByRVA( rva, SymTagBlock, &pBlock ) ) )
    {
        Fatal( "Failed to find symbols by RVA" );
    }
    CComPtr< IDiaSymbol > pscope;
    for ( ; pBlock != NULL; )
    {
        CComPtr< IDiaEnumSymbols > pEnum;
        // local data search
        if ( FAILED( pBlock->findChildren( SymTagNull, NULL, nsNone, &pEnum ) ) )
        {
            Fatal( "Local scope findChildren failed" );
        }
        CComPtr< IDiaSymbol > pSymbol;
        DWORD tag;
        DWORD celt;
        while ( pEnum != NULL &&
                SUCCEEDED( pEnum->Next( 1, &pSymbol, &celt ) ) &&
                celt == 1)
        {
            pSymbol->get_symTag( &tag );
            if ( tag == SymTagData )
            {
                CDiaBSTR name;
                DWORD    kind;
                pSymbol->get_name( &name );
                pSymbol->get_dataKind( &kind );
                if ( name != NULL )
                    wprintf_s( L"\t%s (%s)\n", name, szDataKinds[ kind ] );
            }
            else if ( tag == SymTagAnnotation )
            {
                CComPtr< IDiaEnumSymbols > pValues;
                // local data search
                wprintf_s( L"\tAnnotation:\n" );
                if ( FAILED( pSymbol->findChildren( SymTagNull, NULL, nsNone, &pValues ) ) )
                    Fatal( "Annotation findChildren failed" );
                pSymbol = NULL;
                while ( pValues != NULL &&
                        SUCCEEDED( pValues->Next( 1, &pSymbol, &celt ) ) &&
                        celt == 1 )
                {
                    CComVariant value;
                    if ( pSymbol->get_value( &value ) != S_OK )
                        Fatal( "No value for annotation data." );
                    wprintf_s( L"\t\t%ws\n", value.bstrVal );
                    pSymbol = NULL;
                }
            }
            pSymbol = NULL;
        }
        pBlock->get_symTag( &tag );
        if ( tag == SymTagFunction )    // stop when at function scope
            break;
        // move to lexical parent
        CComPtr< IDiaSymbol > pParent;
        if ( SUCCEEDED( pBlock->get_lexicalParent( &pParent ) )
            && pParent != NULL ) {
            pBlock = pParent;
        }
        else
        {
            Fatal( "Finding lexical parent failed." );
        }
    };
}
```

## <a name="requirements"></a>Wymagania
`Header:`Dia2. h

Biblioteka: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [Symbole i znaczniki symboli](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [Jednostka kompilacji](../../debugger/debug-interface-access/compiland.md)
