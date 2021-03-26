---
title: Opis katalogu szablonów (. VSDIR) | Microsoft Docs
description: Dowiedz się, jak plik opisu katalogu szablonów umożliwia programowi Visual Studio IDE Wyświetlanie folderów, plików VSZ i szablonów skojarzonych z projektem.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bdd21dfa9fe5aae11553bb0268017690aba46fe9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080505"
---
# <a name="template-directory-description-vsdir-files"></a>Opis katalogu szablonu (pliki Vsdir)
Plik opisu katalogu szablonu (. vsdir) to plik tekstowy, który umożliwia zintegrowane środowisko programistyczne (IDE) do wyświetlania folderów, plików kreatora. vsz i plików szablonów, które są skojarzone z projektem w oknach dialogowych. Zawartość zawiera jeden rekord na plik lub folder. Wszystkie pliki. vsdir w lokalizacji, do której się odwołuje, są scalane, chociaż tylko jeden plik. vsdir jest ogólnie dostarczany, aby opisać wiele folderów, kreatorów lub plików szablonów.

 Foldery (podkatalogi), pliki, do których odwołuje się plik. vsdir, i sam plik. vsdir znajdują się w tym samym katalogu. Gdy środowisko IDE uruchamia kreatora lub wyświetla folder lub plik w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** , IDE sprawdza katalog zawierający wykonane pliki, aby określić, czy plik. vsdir jest obecny. Jeśli zostanie znaleziony plik. vsdir, środowisko IDE odczytuje je w celu określenia, czy zawiera wpis dla wykonanego lub wyświetlanego folderu lub pliku. W przypadku znalezienia wpisu środowisko IDE używa informacji w trakcie wykonywania kreatora lub wyświetlania zawartości.

 Poniższy przykład kodu pochodzi z pliku SourceFiles. vsdir w \<EnvSDK> kluczu rejestru \bscprj\bscprj\bscprjprojectitems\ Source_Files:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 W takim przypadku dwa rekordy znajdują się w jednym pliku. Nowy wiersz (znak powrotu karetki) oddziela każdy rekord. Każdy wiersz reprezentuje inny typ pliku. Znak potoku (&#124;) oddziela pola w każdym rekordzie. Pojedynczy katalog może zawierać wiele plików. vsdir o różnych nazwach plików lub jeden plik. vsdir dla każdego typu pliku.

## <a name="fields"></a>Pola
 Poniższa tabela zawiera listę pól określonych dla każdego rekordu.

| Pole | Opis |
| - | - |
| Nazwa ścieżki względnej (RelPathName) | Nazwa folderu, szablonu lub pliku VSZ, na przykład HeaderFile. h lub Kreator. vsz. To pole może również być nazwą używaną do reprezentowania folderu. |
| {clsidPackage} | Identyfikator GUID pakietu VSPackage, który umożliwia dostęp do zlokalizowanych ciągów, takich jak Zlokalizowanename, Description, IconResourceId i SuggestedBaseName, w zasobach biblioteki DLL () satelitarnych w pakietu VSPackage. IconResourceId stosuje się, jeśli nie podano ścieżka dll. **Uwaga:**  To pole jest opcjonalne, chyba że co najmniej jedno z poprzednich pól jest identyfikatorem zasobu. To pole jest zwykle puste dla plików. vsdir, które są zgodne z kreatorami innych firm, które nie lokalizują tekstu. |
| Zlokalizowana | Zlokalizowana nazwa pliku lub Kreatora szablonu. To pole może być ciągiem lub identyfikatorem zasobu w postaci "#ResID". Ta nazwa zostanie wyświetlona w oknie dialogowym **Dodaj nowy element** . **Uwaga:**  Jeśli parametr Lokalizowaćname jest identyfikatorem zasobu, wymagany jest element {clsidPackage}. |
| SortPriority | Liczba całkowita reprezentująca względny priorytet tego pliku lub Kreatora szablonu. Na przykład, jeśli ten element ma wartość 1, ten element będzie wyświetlany obok innych elementów o wartości 1 i przed wszystkie elementy z wartością sortowania równą 2 lub większą.<br /><br /> Priorytet sortowania jest względny dla elementów w tym samym katalogu. Może istnieć więcej niż jeden plik. vsdir w tym samym katalogu. W takim przypadku elementy ze wszystkich <em>.</em> Pliki VSDir w tym katalogu są scalane. Elementy o takim samym priorytecie są wymienione w kolejności leksykograficznych bez uwzględniania wielkości liter dla wyświetlanej nazwy. `_wcsicmp`Funkcja służy do porządkowania elementów.<br /><br /> Elementy nieopisane w plikach. vsdir zawierają numer priorytetu większy niż najwyższy numer priorytetu wymieniony w plikach. vsdir. Wynika to z tego, że te elementy znajdują się na końcu wyświetlonej listy, niezależnie od ich nazwy. |
| Opis | Zlokalizowany Opis pliku lub Kreatora szablonu. To pole może być ciągiem lub identyfikatorem zasobu w postaci "#ResID". Ten ciąg jest wyświetlany w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** , gdy element jest zaznaczony. |
| Ścieżka dll lub {clsidPackage} | Służy do ładowania ikony pliku lub Kreatora szablonu. Ikona jest ładowana jako zasób z pliku DLL lub exe przy użyciu IconResourceId. Plik. dll lub. exe można zidentyfikować za pomocą pełnej ścieżki lub za pomocą identyfikatora GUID pakietu VSPackage. Biblioteka DLL implementacji pakietu VSPackage jest używana do załadowania ikony (a nie satelitarnej biblioteki DLL). |
| IconResourceId | Identyfikator zasobu w bibliotece DLL lub pakietu VSPackage implementacji, który określa ikonę, która ma zostać wyświetlona. |
| Flagi ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS> ) | Służy do wyłączania lub włączania pól **Nazwa** i **Lokalizacja** w oknie dialogowym **Dodaj nowy element** . Wartość pola **flags** jest odpowiednikiem dziesiętnym kombinacji wymaganych flag bitowych.<br /><br /> Gdy użytkownik wybierze element na **nowej** karcie, projekt określa, czy pole Nazwa i pole Lokalizacja są wyświetlane, gdy zostanie wyświetlone okno dialogowe **Dodaj nowy element** . Element, za pomocą pliku. vsdir, może kontrolować tylko to, czy pola są włączone i wyłączone, gdy element jest zaznaczony. |
| SuggestedBaseName | Reprezentuje domyślną nazwę pliku, kreatora lub szablonu. To pole jest ciągiem lub identyfikatorem zasobu w postaci "#ResID". IDE używa tej wartości do podania nazwy domyślnej dla elementu. Ta wartość podstawowa jest dołączana do wartości całkowitej, aby nazwa była unikatowa, na przykład MyFile21. ASP.<br /><br /> W poprzednich listach, Description, ścieżka dll, IconResourceId, Flags i SuggestedBaseNumber dotyczą tylko plików szablonów i kreatora. Te pola nie dotyczą folderów. Ten fakt jest przedstawiony w kodzie w pliku BscPrjProjectItems w \<EnvSDK> kluczu rejestru \BscPrj\BscPrj\BscPrjProjectItems. Ten plik zawiera trzy rekordy (jeden dla każdego folderu) z czterema polami dla każdego rekordu: RelPathName, {clsidPackage}, Lokalizowaćname i SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Podczas tworzenia pliku kreatora należy również wziąć pod uwagę następujące problemy.

- Każde niewymagane pole, dla którego nie ma znaczących danych, powinno zawierać 0 (zero) jako symbol zastępczy.

- Jeśli nie podano zlokalizowanej nazwy, nazwa ścieżki względnej jest używana w pliku Kreatora.

- Ścieżka dll przesłania clsidPackage dla lokalizacji ikony.

- Jeśli nie zdefiniowano żadnej ikony, IDE zastępuje domyślną ikonę pliku, który ma to rozszerzenie.

- Jeśli nie zostanie podana Sugerowana nazwa podstawowa, jest używany element "Project".

- W przypadku usunięcia plików. vsz, folderów lub plików szablonów, należy również usunąć skojarzone z nimi rekordy z pliku. vsdir.

## <a name="see-also"></a>Zobacz też
- [Kreatory](../../extensibility/internals/wizards.md)
- [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
