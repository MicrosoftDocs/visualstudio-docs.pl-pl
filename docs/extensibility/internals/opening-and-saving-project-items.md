---
title: Otwieranie i zapisywanie elementów projektu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbb89d99e401be6bae7d8ee9be8ee33fa7574723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706969"
---
# <a name="opening-and-saving-project-items"></a>Otwieranie i zapisywanie elementów projektu
Po dodaniu nowego typu projektu należy zarządzać otwieraniem i zapisywaniem plików projektów w zintegrowanym [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisku programistycznym (IDE). W poniższych tematach omówiono różne podejścia do otwierania i zapisywania plików.

## <a name="in-this-section"></a>W tej sekcji
- [Wyświetlanie plików za pomocą polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Zawiera szczegółowe wyjaśnienie, w jaki sposób IDE obsługuje polecenie **Otwórz plik** i rolę projektów w odpowiadaniu na to polecenie.

- [Wyświetlanie plików przy użyciu polecenia Otwórz za pomocą](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Zawiera szczegółowe, krok po kroku wyjaśnienie, jak IDE obsługuje **Open With** polecenia, monitując o otwarcie pliku, który ma wybór standardowych edytorów.

- [Instrukcje: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)

 Zawiera instrukcje krok po kroku określające, że pliki określonego typu w projekcie powinny być otwierane przy użyciu edytora specyficznego dla projektu.

- [Instrukcje: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)

 Zawiera instrukcje krok po kroku określające sposób włączania IDE, aby otworzyć standardowy edytor dla plików w typie projektu.

- [Instrukcje: otwieranie edytorów dla otwartych dokumentów](../../extensibility/how-to-open-editors-for-open-documents.md)

 Zawiera instrukcje krok po kroku, aby otworzyć edytor specyficzny dla projektu dla otwartego pliku.

- [Zapisywanie standardowego dokumentu](../../extensibility/internals/saving-a-standard-document.md)

 Zawiera szczegółowe wyjaśnienie, w jaki sposób IDE obsługuje **polecenia Zapisz,** **Zapisz jako**i Zapisz **wszystkie** dla dokumentu otwartego w edytorze standardowym.

- [Zapisywanie niestandardowego dokumentu](../../extensibility/internals/saving-a-custom-document.md)

 Zawiera diagram i szczegółowe wyjaśnienie, w jaki sposób IDE obsługuje **polecenia Zapisz,** **Zapisz jako**i Zapisz **wszystkie** dla dokumentów otwartych w edytorze niestandardowym.

- [Określanie, który edytor służy do otwierania pliku w projekcie](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 W tym artykule omówiono proces, który ide następuje, aby wybrać odpowiedni edytor lub projektant dla pliku.

## <a name="related-sections"></a>Sekcje pokrewne
- [Tworzenie niestandardowych edytorów i projektantów](../../extensibility/creating-custom-editors-and-designers.md)

 Wyświetla listę czterech typów edytorów, które IDE może obsługiwać i zawiera opisy każdego edytora.

- [Project Types (Typy projektów)](../../extensibility/internals/project-types.md)

 W tym artykule omówiono sposób, w jaki projekty kontrolują sposób kompilowania i kompilowania kodu, jak otwierane są edytory i jak elementy projektu są formatowane.
