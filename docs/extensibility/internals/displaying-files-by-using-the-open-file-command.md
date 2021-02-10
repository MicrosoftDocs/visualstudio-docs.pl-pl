---
title: Wyświetlanie plików przy użyciu polecenia Otwórz plik | Microsoft Docs
description: Dowiedz się, w jaki sposób zintegrowane środowisko programistyczne (IDE) programu Visual Studio obsługuje polecenie Otwórz plik w menu plik, aby wyświetlić pliki.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96f92aa921c7bb78511ed685d846e288518258fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946829"
---
# <a name="display-files-by-using-the-open-file-command"></a>Wyświetlanie plików przy użyciu polecenia Otwórz plik
Poniższe kroki opisują, jak środowisko IDE obsługuje polecenie **Otwórz plik** , które jest dostępne w menu **plik** w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . W tym kroku opisano również sposób, w jaki projekty powinny odpowiadać na wywołania pochodzące z tego polecenia.

 Gdy użytkownik kliknie polecenie **Otwórz plik** w menu **plik** i wybierze plik z okna dialogowego **Otwórz plik** , wystąpi następujący proces:

1. Przy użyciu tabeli dokumentu, IDE Określa, czy plik jest już otwarty w projekcie.

    - Jeśli plik jest otwarty, środowisko IDE będzie odpowierzchnię okna.

    - Jeśli plik nie jest otwarty, środowisko IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> zapytania o każdy projekt, aby określić, który projekt może otworzyć plik.

        > [!NOTE]
        > W implementacji projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> , podaj wartość priorytetu, która wskazuje poziom, na którym projekt otwiera plik. Wartości priorytetów są podane w <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> wyliczeniu.

2. Każdy projekt reaguje na poziom priorytetu, który wskazuje istotność, w której ma nastąpić projekt, aby otworzyć plik.

3. Środowisko IDE używa następujących kryteriów do określenia, który projekt otwiera plik:

    - Projekt, który odpowiada z najwyższym priorytetem ( `DP_Intrinsic` ) otwiera plik. Jeśli więcej niż jeden projekt odpowie z tym priorytetem, pierwszy projekt do odpowiedzenia spowoduje otwarcie pliku.

    - Jeśli żaden projekt nie odpowie z najwyższym priorytetem ( `DP_Intrinsic` ), ale wszystkie projekty odpowiadają z tym samym, niższym priorytetem, aktywny projekt otwiera plik. Jeśli żaden projekt nie jest aktywny, pierwszy projekt do odpowiedzi otwiera plik.

    - Jeśli żaden udział w projekcie nie ma własności pliku ( `DP_Unsupported` ), projekt różne pliki otwiera plik.

         Jeśli zostanie utworzone wystąpienie projektu różne pliki, projekt zawsze odpowiada wartości `DP_CanAddAsExternal` . Ta wartość wskazuje, że projekt może otworzyć plik. Ten projekt jest używany do przechowywania otwartych plików, które nie znajdują się w żadnym innym projekcie. Lista elementów w tym projekcie nie jest utrwalona; Ten projekt jest widoczny w **Eksplorator rozwiązań** tylko wtedy, gdy jest używany do otwierania pliku.

         Jeśli projekt różne pliki nie wskazuje, że może otworzyć plik, wystąpienie projektu nie zostało utworzone. W takim przypadku IDE tworzy wystąpienie projektu różne pliki i instruuje projekt, aby otworzył plik.

4. Gdy tylko środowisko IDE określi, który projekt otwiera plik, wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodę dla tego projektu.

5. Projekt zawiera również opcję otwierania pliku przy użyciu edytora specyficznego dla projektu lub edytora standardowego. Aby uzyskać więcej informacji, zobacz [jak: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md) i [instrukcje: otwieranie edytorów standardowych](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Zobacz też
- [Wyświetlanie plików przy użyciu polecenia Otwórz za pomocą](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)
- [Instrukcje: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)
- [Instrukcje: otwieranie edytorów standardowych](../../extensibility/how-to-open-standard-editors.md)
