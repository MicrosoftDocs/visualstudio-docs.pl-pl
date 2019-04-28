---
title: 'Instrukcje: Na pasku stanu aktualizacji | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94ee2d0585892730659943b6dc826ca1b8947510
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63415467"
---
# <a name="how-to-update-the-status-bar"></a>Instrukcje: Aktualizacja paska stanu
**Pasek stanu** pasek sterowania znajduje się w dolnej części wiele okien aplikacji, zawierający co najmniej jeden stan wierszy tekstu lub wskaźniki.

## <a name="to-update-the-status-bar"></a>Aby zaktualizować paska stanu

1. Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> dla każdego obiektu poszczególnych widoku (DocView), zapewniająca edytora, takie jak widok formularza i widoku kodu.

2. Kiedy wywołuje IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, zaktualizuj informacje w **pasek stanu** przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.

    > [!NOTE]
    > Wywołania środowiska IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> tylko kiedy okno dokumentu został początkowo uaktywniony. Pozostały okres czasu, który okna dokumentu jest aktywny, należy zaktualizować **pasek stanu** informacji jako stan zmiany edytora.

## <a name="robust-programming"></a>Skuteczne programowanie
 A **pasek stanu** zawiera cztery oddzielne pola:

- Tekst statusu

- Pasek postępu

- Animowaną ikonę

- Edytor informacji

  Aby uzyskać więcej informacji, zobacz [paski stanu](/cpp/mfc/status-bars).

  IDE automatycznie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> metody usługi <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> wdrożenia po uaktywnieniu okna dokumentu.

  Implementujący pakietu VSPackage jest odpowiedzialny za aktualizowanie tekst statusu na pasku stanu. IDE resetuje ten ciąg na "GOTOWY", jeśli pole tekstowe stan jest ustawiony na pusty tekst ("") w czasie bezczynności.

## <a name="see-also"></a>Zobacz także
- [Paski stanu](/cpp/mfc/status-bars)