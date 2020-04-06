---
title: Wyświetlanie plików za pomocą polecenia Otwórz plik | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc18442c55b6989c4d8668e1425fdd62a2d4b1b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708598"
---
# <a name="display-files-by-using-the-open-file-command"></a>Wyświetlanie plików za pomocą polecenia Otwórz plik
W poniższych krokach opisano sposób obsługi polecenia **Otwórz plik,** które [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]jest dostępne w menu **Plik** w programie . Kroki opisują również, jak projekty powinny reagować na wywołania, które pochodzą z tego polecenia.

 Gdy użytkownik kliknie polecenie **Otwórz plik** w menu **Plik** i wybierze plik z okna dialogowego **Otwórz plik,** następuje następujący proces:

1. Przy użyciu uruchomionej tabeli dokumentów IDE określa, czy plik jest już otwarty w projekcie.

    - Jeśli plik jest otwarty, IDE pojawia się ponownie okna.

    - Jeśli plik nie jest otwarty, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> IDE wywołuje kwerendy każdego projektu, aby określić, który projekt można otworzyć plik.

        > [!NOTE]
        > W implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>projektu , podaj wartość priorytetu, która wskazuje poziom, na którym projekt otwiera plik. Wartości priorytetu są <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> podane w wyliczeniu.

2. Każdy projekt odpowiada z poziomem priorytetu, który wskazuje znaczenie, jakie nakłada na projekt, aby otworzyć plik.

3. IDE używa następujących kryteriów, aby określić, który projekt otwiera plik:

    - Projekt, który odpowiada z najwyższym`DP_Intrinsic`priorytetem ( ) otwiera plik. Jeśli więcej niż jeden projekt odpowiada z tym priorytetem, pierwszy projekt, aby odpowiedzieć otwiera plik.

    - Jeśli żaden projekt nie odpowiada`DP_Intrinsic`z najwyższym priorytetem ( ), ale wszystkie projekty odpowiadają z tym samym, niższym priorytetem, aktywny projekt otwiera plik. Jeśli żaden projekt nie jest aktywny, pierwszy projekt, aby odpowiedzieć otwiera plik.

    - Jeśli żaden projekt nie twierdzi, że jest właścicielem pliku (`DP_Unsupported`), projekt Różne pliki otwiera plik.

         Jeśli zostanie utworzone wystąpienie projektu Różne pliki, projekt zawsze odpowiada `DP_CanAddAsExternal`wartością . Ta wartość wskazuje, że projekt może otworzyć plik. Ten projekt jest używany do mieszczenia otwartych plików, które nie są w żadnym innym projekcie. Lista elementów w tym projekcie nie jest utrwalona; ten projekt jest widoczny w **Eksploratorze rozwiązań** tylko wtedy, gdy jest używany do otwierania pliku.

         Jeśli projekt Różne pliki nie wskazuje, że można otworzyć plik, wystąpienie projektu nie został utworzony. W takim przypadku IDE tworzy wystąpienie projektu Różne pliki i informuje projekt, aby otworzyć plik.

4. Jak tylko IDE określa, który projekt otwiera plik, wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodę w tym projekcie.

5. Następnie projekt ma możliwość otwarcia pliku przy użyciu edytora specyficznego dla projektu lub standardowego edytora. Aby uzyskać więcej informacji, zobacz [Jak: Otwórz edytory specyficzne dla projektu](../../extensibility/how-to-open-project-specific-editors.md) i [Jak: Otwórz edytory standardowe](../../extensibility/how-to-open-standard-editors.md), odpowiednio.

## <a name="see-also"></a>Zobacz też
- [Wyświetlanie plików za pomocą polecenia Otwórz za pomocą](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)
- [Jak: Otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)
- [Jak: Otwórz edytory standardowe](../../extensibility/how-to-open-standard-editors.md)
