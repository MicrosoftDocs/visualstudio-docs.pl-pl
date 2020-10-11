---
title: Przesłonięcia Menedżera zawartości pomocy
description: Dowiedz się więcej na temat zastąpień Menedżera zawartości pomocy, które umożliwiają zmianę domyślnego zachowania podglądu pomocy i funkcji związanych z pomocą w środowisku IDE programu Visual Studio.
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60f4e46d8c43c90759c964dbf01145d876a9f413
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91879063"
---
# <a name="help-content-manager-overrides"></a>Przesłonięcia Menedżera zawartości pomocy

Można zmienić domyślne zachowanie podglądu pomocy i funkcji związanych z pomocą w środowisku IDE programu Visual Studio. Niektóre opcje są określone przez utworzenie pliku [. pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/) w celu ustawienia różnych wartości kluczy rejestru. Inne są ustawiane bezpośrednio w rejestrze.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>Jak kontrolować zachowanie podglądu pomocy przy użyciu pliku. pkgdef

1. Utwórz plik *. pkgdef* z pierwszym wierszem jako `[$RootKey$\Help]` .

2. Dodaj wszystkie lub wszystkie wartości klucza rejestru opisane w poniższej tabeli w oddzielnych wierszach, na przykład `"UseOnlineHelp"=dword:00000001` .

3. Skopiuj plik do pliku *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017 \\<Edition \> \Common7\IDE\CommonExtensions*.

4. Uruchom `devenv /updateconfiguration` w wierszu polecenia dewelopera.

### <a name="registry-key-values"></a>Wartości klucza rejestru

|Wartość klucza rejestru|Type|Dane|Opis|
|------------------|----|----|-----------|
|NewContentAndUpdateService|ciąg|\<http URL for service endpoint\>|Zdefiniuj unikatowy punkt końcowy usługi|
|UseOnlineHelp|Ostatnie|`0` Aby określić pomoc lokalną, `1` Aby określić pomoc online|Zdefiniuj domyślną pomoc w trybie online lub offline|
|OnlineBaseUrl|ciąg|\<http URL for service endpoint\>|Zdefiniuj unikatowy punkt końcowy F1|
|OnlineHelpPreferenceDisabled|Ostatnie|`0` Aby włączyć lub `1` wyłączyć opcję preferencji pomoc online|Wyłącz opcję preferencji pomoc online|
|DisableManageContent|Ostatnie|`0` Aby włączyć lub `1` wyłączyć kartę **Zarządzaj zawartością** w podglądzie pomocy|Wyłącz kartę **Zarządzaj zawartością**|
|DisableFirstRunHelpSelection|Ostatnie|`0` Aby włączyć lub `1` wyłączyć funkcje pomocy, które są konfigurowane podczas pierwszego uruchomienia programu Visual Studio|Wyłącz instalację zawartości przy pierwszym uruchomieniu programu Visual Studio|

### <a name="example-pkgdef-file-contents"></a>Przykład zawartość pliku pkgdef

```pkgdef
[$RootKey$\Help]
"NewContentAndUpdateService"="https://some.service.endpoint"
"UseOnlineHelp"=dword:00000001
"OnlineBaseUrl"="https://some.service.endpoint"
"OnlineHelpPreferenceDisabled"=dword:00000000
"DisableManageContent"=dword:00000000
"DisableFirstRunHelpSelection"=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>Użyj edytora rejestru, aby zmienić zachowanie podglądu pomocy

Poniższe dwa zachowania można kontrolować przez ustawienie wartości klucza rejestru w Edytorze rejestru.

|Zadanie|Klucz rejestru|Wartość|Dane|
|----------|-----|------|----|
|Zastąp priorytet zadania usługi BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na komputerze 64-bitowym) \Microsoft\Help\v2.3|BITSPriority|**pierwszy plan**, **wysoki**, **normalny**lub **niski**|
|Wskaż lokalny magazyn zawartości w udziale sieciowym|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\ v 2.3 \ Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|

## <a name="see-also"></a>Zobacz też

- [Podręcznik administratora podglądu pomocy](../help-viewer/administrator-guide.md)
- [Argumenty wiersza polecenia dla Menedżera zawartości pomocy](../help-viewer/command-line-arguments.md)
- [Podgląd Pomocy firmy Microsoft](../help-viewer/overview.md)