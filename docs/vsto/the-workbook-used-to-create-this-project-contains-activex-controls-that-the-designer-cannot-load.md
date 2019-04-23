---
title: Skoroszyt użyty do tworzenia tego projektu zawiera formanty ActiveX, których projektant nie może załadować
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0087841e7f37d49da40817e1487b8529af1f87df
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089357"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>Skoroszyt użyty do tworzenia tego projektu zawiera formanty ActiveX, których projektant nie może załadować
  Ten błąd jest wyświetlany, gdy dodajesz formant do dokumentu programu Word lub arkusz programu Excel programowo, Zapisz dokument lub skoroszyt, a następnie utwórz nowe rozwiązanie poziomie dokumentu, w oparciu o dokument lub skoroszyt.

 Informacje opisujące typu zarządzanego formantu nie są zapisywane wraz z dokument lub skoroszyt. Podczas tworzenia nowego rozwiązania na podstawie ten dokument lub skoroszyt programu Visual Studio nie ma wystarczających informacji, aby załadować formantu w Projektancie elementu host.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Otwórz dokument lub skoroszyt.

2. Usuwanie kontrolek, które zostały dodane w czasie wykonywania. Można to zrobić, wybierając je w dokumencie lub skoroszycie i naciskając klawisz **Usuń** klucza.

3. Utwórz rozwiązanie poziomu dokumentu oparte na dokumencie lub skoroszycie.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
