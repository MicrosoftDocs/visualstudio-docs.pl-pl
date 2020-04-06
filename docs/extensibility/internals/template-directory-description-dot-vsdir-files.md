---
title: Opis katalogu szablonu (. Vsdir) Pliki | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16ba609d5b05d565a12b38bd19e9a777851ced5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704686"
---
# <a name="template-directory-description-vsdir-files"></a>Opis katalogu szablonu (pliki Vsdir)
Plik opisu katalogu szablonów (vsdir) to plik tekstowy, który umożliwia zintegrowanemu środowisku programistycznemu (IDE) wyświetlanie folderów, plików kreatora .vsz i plików szablonów skojarzonych z projektem w oknach dialogowych. Zawartość zawiera jeden rekord na plik lub folder. Wszystkie pliki vsdir w lokalizacji, do których istnieje odwołanie, są scalane, chociaż tylko jeden plik vsdir jest zazwyczaj dostarczany w celu opisania wielu folderów, kreatorów lub plików szablonów.

 Foldery (podkatalogi), pliki, do których odwołuje się plik vsdir, oraz sam plik vsdir znajdują się w tym samym katalogu. Gdy IDE uruchamia kreatora lub wyświetla folder lub plik w oknie dialogowym **Nowy projekt** lub Dodaj **nowy element,** IDE sprawdza katalog zawierający wykonane pliki, aby ustalić, czy plik vsdir jest obecny. Jeśli zostanie znaleziony plik vsdir, IDE odczytuje go, aby ustalić, czy zawiera wpis dla wykonanego lub wyświetlanego folderu lub pliku. Jeśli zostanie znaleziony wpis, IDE używa informacji w wykonywaniu kreatora lub wyświetlania zawartości.

 Poniższy przykład kodu pochodzi z pliku SourceFiles.vsdir w> \<EnvSDK\BscPrj\BscPrj\BscPrjProjectItems\Source_Files klucz rejestru:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 W takim przypadku dwa rekordy znajdują się w jednym pliku. Nowy wiersz (znak powrotu karetki) oddziela każdy rekord. Każdy wiersz reprezentuje inny typ pliku. Znak potoku (&#124;) oddziela pola w każdym rekordzie. Jeden katalog może zawierać wiele plików vsdir, które mają różne nazwy plików, lub można mieć jeden plik vsdir dla każdego typu pliku.

## <a name="fields"></a>Pola
 W poniższej tabeli wymieniono pola określone dla każdego rekordu.

| Pole | Opis |
| - | - |
| Nazwa ścieżki względnej (RelPathName) | Nazwa folderu, szablonu lub pliku .vsz, takiego jak HeaderFile.h lub MyWizard.vsz. To pole może być również nazwą używaną do reprezentowania folderu. |
| {clsidPackage} | Identyfikator GUID programu VSPackage, który umożliwia dostęp do zlokalizowanych ciągów, takich jak LocalizedName, Description, IconResourceId i SuggestedBaseName, w zasobach biblioteki łącza dynamicznego (DLL) programu VSPackage. IconResourceId stosuje się, jeśli DLLPath nie jest podany. **Uwaga:**  To pole jest opcjonalne, chyba że jedno lub więcej poprzednich pól jest identyfikatorem zasobu. To pole jest zazwyczaj puste dla plików vsdir, które odpowiadają kreatorom innych firm, które nie lokalizują ich tekstu. |
| Localizedname | Zlokalizowana nazwa pliku szablonu lub kreatora. To pole może być ciągiem lub identyfikatorem zasobu formularza "#ResID". Ta nazwa jest wyświetlana w oknie dialogowym **Dodawanie nowego elementu.** **Uwaga:**  Jeśli LocalizedName jest identyfikatorem zasobu, to {clsidPackage} jest wymagane. |
| SortPriority (SortPriority) | Liczba całkowita reprezentująca względny priorytet tego pliku szablonu lub kreatora. Na przykład jeśli ten element ma wartość 1, ten element jest wyświetlany obok innych elementów o wartości 1 i przed wszystkimi elementami o wartości sortowania 2 lub większej.<br /><br /> Priorytet sortowania jest względem elementów w tym samym katalogu. W tym samym katalogu może znajdować się więcej niż jeden plik vsdir. W takim przypadku elementy ze wszystkich <em>.</em> pliki vsdir w tym katalogu są scalane. Elementy o tym samym priorytecie są wyświetlane w kolejności leksykograficznej bez uwzględniania wielkości liter wyświetlanej nazwy. Funkcja `_wcsicmp` służy do zamawiania elementów.<br /><br /> Elementy nieopisane w plikach .vsdir zawierają numer priorytetu większy niż numer o najwyższym priorytecie wymieniony w plikach vsdir. W rezultacie te elementy znajdują się na końcu wyświetlanej listy, niezależnie od ich nazwy. |
| Opis | Zlokalizowany opis pliku szablonu lub kreatora. To pole może być ciągiem lub identyfikatorem zasobu formularza "#ResID". Ten ciąg pojawia się w oknie dialogowym **Nowy projekt** lub Dodaj **nowy element** po wybraniu elementu. |
| DLLPath lub {clsidPackage} | Służy do ładowania ikony pliku szablonu lub kreatora. Ikona jest ładowana jako zasób z pliku .dll lub .exe przy użyciu identyfikatora IconResourceId. Ten plik .dll lub .exe można zidentyfikować za pomocą pełnej ścieżki lub przy użyciu identyfikatora GUID vsPackage. Biblioteka DLL implementacji programu VSPackage służy do ładowania ikony (nie biblioteki DLL satelity). |
| IconResourceId (łańz) | Identyfikator zasobu w biblioteki DLL lub BIBLIOTEKI DLL implementacji VSPackage, który określa ikonę do wyświetlenia. |
| Flagi<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>( ) | Służy do wyłączania lub włączania pól **Nazwa** i **lokalizacja** w oknie dialogowym **Dodawanie nowego elementu.** Wartość pola **Flagi** jest dziesiętnym odpowiednikiem kombinacji wymaganych flag bitowych.<br /><br /> Gdy użytkownik wybierze element na karcie **Nowy,** projekt określa, czy pole Nazwa i Pole Lokalizacja są wyświetlane po pierwszym wyświetleniu okna dialogowego **Dodawanie nowego elementu.** Element za pośrednictwem pliku vsdir może kontrolować tylko, czy pola są włączone, a nie wyłączone, gdy element jest zaznaczony. |
| Sugerowana nazwa bazowa | Reprezentuje domyślną nazwę pliku, kreatora lub szablonu. To pole jest ciągiem lub identyfikatorem zasobu formularza "#ResID". IDE używa tej wartości, aby podać domyślną nazwę elementu. Ta wartość bazowa jest dołączana z wartością całkowitą, aby nazwa była unikatowa, na przykład MyFile21.asp.<br /><br /> Na poprzedniej liście Opis, Ścieżka DLLPath, IconResourceId, Flagi i Sugerowana liczba baz dotyczy tylko plików szablonów i kreatorów. Te pola nie mają zastosowania do folderów. Fakt ten jest zilustrowany w kodzie w pliku BscPrjProjectItems w kluczu rejestru \<EnvSDK>\BscPrj\BscPrj\BscPrjProjectItems. Ten plik zawiera trzy rekordy (po jednym dla każdego folderu) z czterema polami dla każdego rekordu: RelPathName, {clsidPackage}, LocalizedName i SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Podczas tworzenia pliku kreatora należy również wziąć pod uwagę następujące problemy.

- Każde niepodane pole, dla którego nie ma znaczących danych, powinno zawierać 0 (zero) jako symbol zastępczy.

- Jeśli nie podano zlokalizowanej nazwy, w pliku kreatora jest używana nazwa ścieżki względnej.

- DLLPath zastępuje clsidPackage dla lokalizacji ikony.

- Jeśli żadna ikona nie jest zdefiniowana, IDE zastępuje domyślną ikonę dla pliku, który ma to rozszerzenie.

- Jeśli nie podano sugerowanej nazwy podstawowej, używana jest wartość "Projekt".

- W przypadku usunięcia plików, folderów lub plików szablonów vsz należy również usunąć skojarzone z nimi rekordy z pliku vsdir.

## <a name="see-also"></a>Zobacz też
- [Kreatory](../../extensibility/internals/wizards.md)
- [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
