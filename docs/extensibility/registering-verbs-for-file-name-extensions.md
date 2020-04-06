---
title: Rejestrowanie zleceń dla rozszerzeń nazw plików | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac2854f1799075cc14d9beb557335be5228be21d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701531"
---
# <a name="register-verbs-for-file-name-extensions"></a>Rejestrowanie zleceń dla rozszerzeń nazw plików
Skojarzenie rozszerzenia nazwy pliku z aplikacją zazwyczaj ma preferowaną akcję, która występuje, gdy użytkownik kliknie dwukrotnie plik. Ta preferowana akcja jest powiązana z czasownikiem, na przykład otwartym, który odpowiada akcji.

 Zlecenia skojarzone z identyfikatorem programowym (ProgID) dla rozszerzenia można rejestrować przy użyciu klucza Powłoki znajdującego się w **HKEY_CLASSES_ROOT\{progid}\shell**. Aby uzyskać więcej informacji, zobacz [Typy plików](/windows/desktop/shell/fa-file-types).

## <a name="register-standard-verbs"></a>Rejestrowanie czasowników standardowych
 System operacyjny rozpoznaje następujące zlecenia standardowe:

- Otwarcie

- Edytuj

- Graj.

- Drukuj

- Wersja zapoznawcza

  Jeśli to możliwe, zarejestruj czasownik standardowy. Najczęstszym wyborem jest czasownik Otwarty. Zlecenia Edycja należy używać tylko wtedy, gdy istnieje wyraźna różnica między otwarciem pliku a edycją pliku. Na przykład otwarcie pliku *.htm* wyświetla go w przeglądarce, podczas gdy edycja pliku *.htm* uruchamia edytor HTML. Zlecenia standardowe są zlokalizowane w ustawieniach regionalnych systemu operacyjnego.

> [!NOTE]
> Podczas rejestrowania zleceń standardowych nie należy ustawiać wartości domyślnej dla klucza Otwórz. Wartość domyślna zawiera ciąg wyświetlania w menu. System operacyjny dostarcza ten ciąg dla zleceń standardowych.

 Pliki projektu powinny być zarejestrowane, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aby rozpocząć nowe wystąpienie, gdy użytkownik otwiera plik. Poniższy przykład ilustruje standardową [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] rejestrację czasownika dla projektu.

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 Aby otworzyć plik w istniejącym wystąpieniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], zarejestruj klucz DDEEXEC. Poniższy przykład ilustruje standardową [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] rejestrację czasownika dla pliku *cs.*

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>Ustawianie zlecenia domyślnego
 Zleceniem domyślnym jest akcja wykonywana, gdy użytkownik kliknie dwukrotnie plik w Eksploratorze Windows. Zleceniem domyślnym jest zlecenie określone jako wartość domyślna dla **HKEY_CLASSES_ROOT\\*klucza progid*\Shell.** Jeśli nie określono żadnej wartości, zlecenie domyślne jest pierwszym zleceniem określonym na liście **\\*kluczy*HKEY_CLASSES_ROOT progid \Shell.**

> [!NOTE]
> Jeśli planujesz zmienić domyślny zlecenie dla rozszerzenia we wdrożeniu side-by-side, należy wziąć pod uwagę wpływ na instalację i usuwanie. Podczas instalacji oryginalna wartość domyślna jest zastępowany.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie skojarzeniami plików obok siebie](../extensibility/managing-side-by-side-file-associations.md)
