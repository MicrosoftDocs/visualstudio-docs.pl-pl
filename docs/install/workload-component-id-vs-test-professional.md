---
title: Visual Studio Test Professional obciążenia i identyfikatory składników
titleSuffix: ''
description: Identyfikatory obciążeń i składników programu Visual Studio umożliwia podanie zintegrowane narzędzia do testowania generalist testerów
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 09/23/2019
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: 70c03438-8434-4921-ada0-c172519af431
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
ms.openlocfilehash: d61105a16919e8384aad961d62a81ff3a8688b25
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213652"
---
# <a name="visual-studio-test-professional-component-directory"></a>Visual Studio Test Professional katalog składników

Tabele na tej stronie listy identyfikatorów, w której można zainstalować program Visual Studio przy użyciu wiersza polecenia lub można określić jako zależności w manifestu VSIX. Należy pamiętać, że dodamy dodatkowe składniki, jak wydaniu aktualizacji do programu Visual Studio.

Ponadto należy pamiętać, że informacje o stronie:

* Każde obciążenie ma osobny rozdział, następuje identyfikator obciążenia i tabeli składników, które są dostępne dla obciążenia.
* Domyślnie **wymagane** składniki zostaną zainstalowane po zainstalowaniu obciążenia.
* Jeśli chcesz, możesz także zainstalować **zalecane** i **opcjonalnie** składników.
* Dodaliśmy również sekcję, która zawiera listę dodatkowych składników, które nie są powiązane z dowolnych obciążeń.

Po ustawieniu współzależności w manifeście VSIX tylko należy określić identyfikatory składników. Użyj tabel na tej stronie, aby określić nasze zależności minimalnej składnika. W niektórych scenariuszach to oznaczać, że należy określić tylko jeden składnik z obciążenia. W innych przypadkach może oznaczać, możesz określić wiele składników z pojedynczego obciążenia lub wielu składników z wielu obciążeń. Aby uzyskać więcej informacji, zobacz [How to: Migrowanie projektów rozszerzalności do strony](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) programu Visual Studio 2017.

Aby uzyskać więcej informacji na temat używania tych identyfikatorów, zobacz [Użyj parametry wiersza polecenia, aby zainstalować program Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) strony. I dla listy, obciążenie i identyfikatorów składników dla innych produktów, zobacz [Visual Studio 2017 obciążenia i identyfikatory składnika](workload-and-component-ids.md) strony.

## <a name="test-professional"></a>Test Professional

**#C1** Microsoft.VisualStudio.Workload.TestProfessional

**Opis:** Test Professional zapewnia zintegrowane narzędzia do testowania przeznaczone dla testerów ogólnych, które ułatwiają im ich testowanie w całym cyklu testowania.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.6.27406.0 | Wymagane
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.6.27406.0 | Wymagane

## <a name="unaffiliated-components"></a>Składniki nie podlega

Są to składniki, które nie są uwzględniane przy użyciu dowolnego obciążenia, ale można wybrać jako poszczególnych składników.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
n/d | n/d | n/d

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
* [Podręcznik administratora w usłudze Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
