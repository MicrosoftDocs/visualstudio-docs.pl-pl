---
title: Visual Studio 2017 klienta opinii obciążeń i składników identyfikatorów
titleSuffix: ''
description: Identyfikatory obciążeń i składników programu Visual Studio umożliwiają przesyłanie bogatych opinii dotyczących usługom DevOps platformy Azure lub serwera Team Foundation Server
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.assetid: 7392a100-100c-458c-9394-828695109015
ms.workload:
- multiple
ms.openlocfilehash: 6631027d604a9ac531211814109deaf309c18732
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066720"
---
# <a name="visual-studio-feedback-client-2017-component-directory"></a>Visual Studio 2017 klienta opinii składników katalogu

Tabele na tej stronie listy identyfikatorów, w której można zainstalować program Visual Studio przy użyciu wiersza polecenia lub można określić jako zależności w manifestu VSIX. Należy pamiętać, że dodamy dodatkowe składniki, jak wydaniu aktualizacji do programu Visual Studio.

Ponadto należy pamiętać, że informacje o stronie:

* Każde obciążenie ma osobny rozdział, następuje identyfikator obciążenia i tabeli składników, które są dostępne dla obciążenia.
* Domyślnie **wymagane** składniki zostaną zainstalowane po zainstalowaniu obciążenia.
* Jeśli chcesz, możesz także zainstalować **zalecane** i **opcjonalnie** składników.
* Dodaliśmy również sekcję, która zawiera listę dodatkowych składników, które nie są powiązane z dowolnych obciążeń.

Po ustawieniu współzależności w manifeście VSIX tylko należy określić identyfikatory składników. Użyj tabel na tej stronie, aby określić nasze zależności minimalnej składnika. W niektórych scenariuszach to oznaczać, że należy określić tylko jeden składnik z obciążenia. W innych przypadkach może oznaczać, możesz określić wiele składników z pojedynczego obciążenia lub wielu składników z wielu obciążeń. Aby uzyskać więcej informacji, zobacz [instrukcje: Migrowanie projektów rozszerzalności do programu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) strony.

Aby uzyskać więcej informacji na temat używania tych identyfikatorów, zobacz [Użyj parametry wiersza polecenia, aby zainstalować program Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) strony. I dla listy, obciążenie i identyfikatorów składników dla innych produktów, zobacz [Visual Studio 2017 obciążenia i identyfikatory składnika](workload-and-component-ids.md) strony.

## <a name="feedback-client"></a>Feedback Client

**ID:** Microsoft.VisualStudio.Workload.FeedbackClient

**Opis:** Feedback client umożliwia uczestnikom projektu przesyłanie bogatych opinii usługom DevOps platformy Azure lub serwera Team Foundation Server.

### <a name="components-included-by-this-workload"></a>Składniki przez to obciążenie

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.6.27406.0 | Wymagane

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
