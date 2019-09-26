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
ms.openlocfilehash: 27feb1c6a85740d8a9287ce3a2a47800595e178a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253780"
---
# <a name="the-workbook-used-to-create-this-project-contains-activex-controls-that-the-designer-cannot-load"></a>Skoroszyt użyty do tworzenia tego projektu zawiera formanty ActiveX, których projektant nie może załadować
  Ten błąd jest wyświetlany, gdy dodasz kontrolkę do dokumentu programu Word lub arkusza programu Excel programowo, Zapisz dokument lub skoroszyt, a następnie utwórz nowe rozwiązanie na poziomie dokumentu na podstawie dokumentu lub skoroszytu.

 Informacje opisujące typ zarządzany kontrolki nie są zapisywane wraz z dokumentem lub skoroszytem. Gdy tworzysz nowe rozwiązanie na podstawie tego dokumentu lub skoroszytu, program Visual Studio nie ma wystarczających informacji do załadowania formantu w projektancie elementów hosta.

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Otwórz dokument lub skoroszyt.

2. Usuń kontrolki, które zostały dodane w czasie wykonywania. Można to zrobić, zaznaczając je w dokumencie lub skoroszycie i naciskając klawisz **delete** .

3. Utwórz rozwiązanie na poziomie dokumentu na podstawie dokumentu lub skoroszytu.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie projektów pakietu Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
