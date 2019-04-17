---
title: Opis katalogu szablonu (. Pliki Vsdir) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0bcd3855b5dd2fc701b78c5745a9053d19dc7fcf
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658256"
---
# <a name="template-directory-description-vsdir-files"></a>Opis katalogu szablonu (pliki Vsdir)
Plik opis katalogu szablonu (vsdir) to plik tekstowy, który umożliwia zintegrowanego środowiska programistycznego (IDE), aby wyświetlić folderów, plików .vsz kreatora i plików szablonów, które są skojarzone z projektem w oknach dialogowych. Zawartość obejmują jeden rekord w pliku lub folderu. Wszystkich plików .vsdir w lokalizacji, do którego istnieje odwołanie są scalane, mimo że .vsdir tylko jeden plik jest zazwyczaj podawana do opisania wiele folderów, pliki szablonów lub kreatorów.

 Foldery (w podkatalogach), pliki, które są określone w pliku .vsdir i sam plik .vsdir znajdują się w tym samym katalogu. Gdy IDE uruchamia Kreator lub wyświetla folderu lub pliku w **nowy projekt** lub **Dodaj nowy element** okien dialogowych, IDE sprawdza, czy katalog, który zawiera pliki wykonane, aby ustalić, czy plik .vsdir jest obecne. Jeśli zostanie znaleziony plik .vsdir, IDE odczytuje go, aby ustalić, czy zawiera on wpis dla wykonany lub wyświetlanych folderu lub pliku. Jeśli wpis zostanie znaleziony, IDE używa tych informacji w wykonanie kreatora lub wyświetlanie zawartości.

 Poniższy przykładowy kod pochodzi z pliku SourceFiles.vsdir w \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems\Source_Files klucz rejestru:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 W takim przypadku dwa rekordy są w jednym pliku. Nowy wiersz (znaku powrotu karetki) oddziela każdego rekordu. Każdy wiersz reprezentuje inny typ pliku. Potok (&#124;) rozdziela pola w każdym rekordzie. Jeden katalog może zawierać wiele plików .vsdir, które mają różne nazwy plików lub może mieć jeden plik .vsdir, dla każdego typu pliku.

## <a name="fields"></a>Pola
 Poniższa lista zawiera pola określone dla każdego rekordu.

| Pole | Opis |
| - | - |
| Nazwa ścieżki względnej (RelPathName) | Nazwa pliku folderu, szablonu lub .vsz, takie jak HeaderFile.h lub MyWizard.vsz. To pole może być również nazwa używana do reprezentowania folderem. |
| {clsidPackage} | Identyfikator GUID pakietu VSPackage, który umożliwia dostęp do zlokalizowanych ciągów, takich jak LocalizedName, opis, IconResourceId i SuggestedBaseName, w ramach pakietu VSPackage satelitarnej dołączana dynamicznie biblioteka (DLL) zasobów. IconResourceId ma zastosowanie, jeśli nie zostanie dostarczona ścieżka dll. **Uwaga:**  To pole jest opcjonalne, chyba że co najmniej jeden poprzednie pola Identyfikator zasobu. To pole jest zwykle puste w przypadku plików .vsdir, które odpowiadają za pomocą kreatorów innych firm, które nie jest lokalizowany ich tekst. |
| LocalizedName | Zlokalizowana nazwa pliku szablonu lub kreatora. To pole może być ciąg lub identyfikator zasobu formularza "#ResID". Ta nazwa będzie wyświetlana w **Dodaj nowy element** okno dialogowe. **Uwaga:**  Jeśli LocalizedName jest identyfikatorem zasobu {clsidPackage} jest wymagana. |
| SortPriority | Liczba całkowita reprezentująca względny priorytet tej pliku szablonu lub kreatora. Na przykład jeśli ten element ma wartość 1, ten element jest wyświetlany obok innych elementów o wartości 1 i wcześniejsze wszystkie elementy z wartością sortowania 2 lub większy.<br /><br /> Priorytet sortowania jest określana względem elementów w tym samym katalogu. Może istnieć więcej niż jeden plik .vsdir w tym samym katalogu. W takim przypadku elementy ze wszystkich <em>.</em> pliki vsdir, w tym katalogu są scalane. Elementy z tym samym priorytecie są wyświetlane w porządku leksykograficznym bez uwzględniania wielkości liter nazwę wyświetlaną. `_wcsicmp` Funkcja jest używana w celu uporządkowania elementów.<br /><br /> Elementy, które nie zostały opisane w plikach .vsdir obejmują większy niż najwyższy priorytet, na liście plików .vsdir priorytety. Wynik jest, że te elementy są na końcu wyświetlonej listy, niezależnie od ich nazwy. |
| Opis | Zlokalizowany opis pliku szablonu lub kreatora. To pole może być ciąg lub identyfikator zasobu formularza "#ResID". Ten ciąg jest wyświetlana w **nowy projekt** lub **Dodaj nowy element** okno dialogowe, gdy element jest zaznaczony. |
| DLLPath lub {clsidPackage} | Używane do ładowania ikony dla pliku szablonu lub kreatora. Ikona jest ładowana jako zasób z pliku .dll lub .exe przy użyciu IconResourceId. Ten plik .dll i .exe można zidentyfikować za pomocą pełną ścieżkę lub przy użyciu identyfikatora GUID pakietu VSPackage. Implementacja DLL pakietu VSPackage jest używana do ładowania ikona (nie satelitarną bibliotekę DLL). |
| IconResourceId | Identyfikator zasobu w pliku DLL lub pakietu VSPackage implementacji biblioteki DLL, który określa ikonę do wyświetlenia. |
| Flagi (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>) | Pozwala włączyć lub wyłączyć **nazwa** i **lokalizacji** pola na **Dodaj nowy element** okno dialogowe. Wartość **flagi** pola jest wartość dziesiętna kombinacja flag bitowych wymagane.<br /><br /> Gdy użytkownik wybierze element na **New** kartę, projektu określa, czy pola nazwy i lokalizacji są wyświetlane podczas **Dodaj nowy element** najpierw zostanie wyświetlone okno dialogowe. Element, za pomocą plików .vsdir, można kontrolować tylko czy pola są włączone i wyłączone, gdy element jest zaznaczony. |
| SuggestedBaseName | Reprezentuje nazwę domyślnego pliku, kreatora lub szablonu. To pole jest ciągiem lub identyfikator zasobu formularza "#ResID". IDE używa tej wartości, aby podać nazwę domyślnej dla elementu. Ta wartość podstawowa jest dołączany wraz z wartością całkowitą z zakresu unikatowość nazwy, takie jak MyFile21.asp.<br /><br /> Na poprzedniej liście opis, ścieżka dll, IconResourceId, flag i SuggestedBaseNumber dotyczą tylko plików szablonów i kreatora. Te pola nie są stosowane do folderów. Ten fakt zilustrowano w kodzie w pliku BscPrjProjectItems w \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems klucza rejestru. Ten plik zawiera trzy rekordy, (po jednym dla każdego folderu) przy użyciu cztery pola dla każdego rekordu: RelPathName, {clsidPackage} LocalizedName i SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Podczas tworzenia pliku kreatora, należy również rozważyć następujące kwestie.

-   Wszystkie pole Niewymagane, dla których nie ma żadnych istotnych danych powinny zawierać wartość 0 (zero) jako symbolu zastępczego.

-   Jeśli nie podano żadnej zlokalizowanej nazwy, nazwa ścieżka względna jest używana w pliku kreatora.

-   Ścieżka dll zastępuje clsidPackage dla lokalizacji ikony.

-   Jeśli nie zdefiniowano żadnej ikony, IDE zastępuje domyślną ikonę pliku z tego rozszerzenia.

-   Jeśli nie podano żadnych sugerowane nazwy podstawowej, "Projekt" jest używana.

-   Jeśli usuniesz plików .vsz, foldery lub pliki szablonów, należy także usunąć ich skojarzonych rekordów z pliku .vsdir.

## <a name="see-also"></a>Zobacz też
- [Kreatory](../../extensibility/internals/wizards.md)
- [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)