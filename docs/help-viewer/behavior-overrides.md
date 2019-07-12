---
title: Przesłonięcia menedżera zawartości pomocy
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c03d631be1bc4a38e514e1019fa230775427a53
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825093"
---
# <a name="help-content-manager-overrides"></a>Przesłonięcia menedżera zawartości pomocy

Można zmienić domyślne zachowanie w Podglądzie pomocy i pomocy funkcjach dostępnych w środowisku IDE programu Visual Studio. Niektóre opcje są określone przez utworzenie [.pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/) pliku można ustawić różne wartości klucza rejestru. Inne są ustawiane bezpośrednio w rejestrze.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>Jak kontrolować zachowanie podglądu pomocy przy użyciu pliku pkgdef

1. Tworzenie *.pkgdef* plik z pierwszego wiersza jako `[$RootKey$\Help]`.

2. Dodaj wybrane lub wszystkie wartości klucza rejestru opisanego w poniższej tabeli opisano w osobnych wierszach, na przykład `"UseOnlineHelp"=dword:00000001`.

3. Skopiuj plik do *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\\< wersja\>\Common7\IDE\CommonExtensions*.

4. Uruchom `devenv /updateconfiguration` w wierszu polecenia dla deweloperów.

### <a name="registry-key-values"></a>Wartości kluczy rejestru

|Wartość klucza rejestru|Typ|Dane|Opis|
|------------------|----|----|-----------|
|NewContentAndUpdateService|string|\<adres URL HTTP dla punktu końcowego usługi\>|Definiowanie punktu końcowego, unikatowa usługa|
|UseOnlineHelp|dword|`0` Aby określić pomocy lokalnej `1` do określenia Pomoc online|Zdefiniować domyślne pomocy online lub offline|
|OnlineBaseUrl|string|\<adres URL HTTP dla punktu końcowego usługi\>|Zdefiniuj unikatowe końcowy F1|
|OnlineHelpPreferenceDisabled|dword|`0` Aby włączyć lub `1` wyłączyć opcja preferencji Pomoc online|Wyłącz opcja preferencji Pomoc online|
|DisableManageContent|dword|`0` Aby włączyć lub `1` wyłączyć **zarządzanie zawartością** karty w Podglądzie pomocy|Wyłącz **zarządzanie zawartością** kartę|
|DisableFirstRunHelpSelection|dword|`0` Aby włączyć lub `1` można wyłączyć funkcji pomocy, które są skonfigurowane przy pierwszym uruchomieniu programu Visual Studio|Wyłączyć możliwość instalacji zawartości podczas pierwszego uruchomienia programu Visual Studio|

### <a name="example-pkgdef-file-contents"></a>Zawartość pliku .pkgdef przykład

```pkgdef
[$RootKey$\Help]
"NewContentAndUpdateService"="https://some.service.endpoint"
"UseOnlineHelp"=dword:00000001
"OnlineBaseUrl"="https://some.service.endpoint"
"OnlineHelpPreferenceDisabled"=dword:00000000
"DisableManageContent"=dword:00000000
"DisableFirstRunHelpSelection"=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>Użyj Edytora rejestru, aby zmienić zachowanie podglądu pomocy

Następujące dwa zachowania mogą być kontrolowane przez ustawienie wartości klucza rejestru w Edytorze rejestru.

|Zadanie|Klucz rejestru|Wartość|Dane|
|----------|-----|------|----|
|Zastąp priorytet zadania usługi BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (na klawiaturze machine)\Microsoft\Help\v2.3 64-bitowych|BITSPriority|**pierwszy plan**, **wysokiej**, **normalne**, lub **niski**|
|Wskaż magazynu zawartości lokalnej w udziale sieciowym|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\ v2.3\Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|

## <a name="see-also"></a>Zobacz także

- [Podręcznik administratora programu Podgląd pomocy](../help-viewer/administrator-guide.md)
- [Argumenty wiersza polecenia dla menedżera zawartości pomocy](../help-viewer/command-line-arguments.md)
- [Podgląd Pomocy firmy Microsoft](../help-viewer/overview.md)