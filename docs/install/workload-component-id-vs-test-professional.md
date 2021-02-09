---
title: Visual Studio Test Professional obciążenia i identyfikatory składników
titleSuffix: ''
description: Użyj obciążeń i identyfikatorów składników programu Visual Studio, aby zapewnić zintegrowane narzędzia do testowania dla testerów ogólnych
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.date: 03/16/2020
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: 70c03438-8434-4921-ada0-c172519af431
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
open_to_public_contributors: false
ms.openlocfilehash: ee8d3d91f5079e23d5a0342c58b2db5a70e45f64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886473"
---
# <a name="visual-studio-test-professional-component-directory"></a>Visual Studio Test Professional katalog składników

Tabele na tej stronie wyświetlają identyfikatory, których można użyć do zainstalowania programu Visual Studio przy użyciu wiersza polecenia lub można określić jako zależność w manifeście VSIX. Należy pamiętać, że po udostępnieniu aktualizacji dla programu Visual Studio zostaną dodane dodatkowe składniki.

Należy również zwrócić uwagę na następujące kwestie dotyczące strony:

* Każde obciążenie ma własną sekcję, a następnie identyfikator obciążenia oraz tabelę składników, które są dostępne dla obciążenia.
* Domyślnie **wymagane** składniki zostaną zainstalowane po zainstalowaniu obciążenia.
* Jeśli wybierzesz opcję, możesz również zainstalować **zalecane** i **opcjonalne** składniki.
* Dodaliśmy również sekcję, która zawiera dodatkowe składniki, które nie są powiązane z żadnym obciążeniem.

Podczas ustawiania zależności w manifeście VSIX należy określić tylko identyfikatory składników. Użyj tabel na tej stronie, aby określić nasze minimalne zależności składników. W niektórych scenariuszach może to oznaczać, że należy określić tylko jeden składnik z obciążenia. W innych scenariuszach może oznaczać, że należy określić wiele składników z pojedynczego obciążenia lub wielu składników z wielu obciążeń. Aby uzyskać więcej informacji, zobacz stronę [How to: migruje Projekty rozszerzalności do programu Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) .

Aby uzyskać więcej informacji na temat korzystania z tych identyfikatorów, zobacz temat [używanie Command-Line parametrów w celu zainstalowania strony programu Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) . Aby uzyskać listę identyfikatorów obciążeń i składników dla innych produktów, zobacz stronę [obciążenia i identyfikatory składników programu Visual Studio 2017](workload-and-component-ids.md) .

## <a name="test-professional"></a>Test Professional

**Identyfikator:** Microsoft. VisualStudio. obciążeni. TestProfessional

**Opis:** Test Professional zapewnia zintegrowane narzędzia do testowania przeznaczone dla testerów ogólnych, które ułatwiają im ich testowanie w całym cyklu testowania.

### <a name="components-included-by-this-workload"></a>Składniki zawarte w tym obciążeniu

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft. VisualStudio. Component. TestTools. FeedbackClient | Microsoft Feedback Client | 15.6.27406.0 | Wymagane
Microsoft. VisualStudio. Component. TestTools. MicrosoftTestManager | Microsoft Test Manager | 15.6.27406.0 | Wymagane

## <a name="unaffiliated-components"></a>Niestowarzyszone składniki

Są to składniki, które nie są uwzględnione w obciążeniu, ale mogą być wybierane jako poszczególne składniki.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
nie dotyczy | nie dotyczy | nie dotyczy

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
