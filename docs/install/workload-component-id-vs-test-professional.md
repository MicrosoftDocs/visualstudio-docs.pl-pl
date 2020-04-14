---
title: Obciążenie i identyfikatory składników programu Visual Studio Test Professional
titleSuffix: ''
description: Korzystanie z obciążenia programu Visual Studio i identyfikatorów składników w celu zapewnienia zintegrowanych narzędzi testujących dla testerów ogólnych
author: ornellaalt
ms.author: ornella
manager: jillfra
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
ms.openlocfilehash: 61a52d98f695a6420dd6081117b8c6c4e83ae0a4
ms.sourcegitcommit: 22deb247ad951e4971f27fdab413b158415d0584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81276217"
---
# <a name="visual-studio-test-professional-component-directory"></a>Katalog składników programu Visual Studio Test Professional

Tabele na tej stronie listy identyfikatorów, których można użyć do zainstalowania programu Visual Studio przy użyciu wiersza polecenia lub które można określić jako zależność w manifeście VSIX. Należy zauważyć, że dodamy dodatkowe składniki podczas wydawania aktualizacji programu Visual Studio.

Zwróć również uwagę na następujące informacje na temat strony:

* Każde obciążenie ma własną sekcję, a następnie identyfikator obciążenia i tabelę składników, które są dostępne dla obciążenia.
* Domyślnie **wymagane** składniki zostaną zainstalowane podczas instalowania obciążenia.
* W tym przypadku można również zainstalować składniki **Zalecane** i **Opcjonalne.**
* Dodaliśmy również sekcję zawierającą listę dodatkowych składników, które nie są powiązane z żadnym obciążeniem.

Po ustawieniu zależności w manifeście VSIX należy określić tylko identyfikatory składników. Użyj tabel na tej stronie, aby określić nasze minimalne zależności składników. W niektórych scenariuszach może to oznaczać, że można określić tylko jeden składnik z obciążenia. W innych scenariuszach może to oznaczać, że można określić wiele składników z jednego obciążenia lub wiele składników z wielu obciążeń. Aby uzyskać więcej informacji, zobacz [how to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) page.

Aby uzyskać więcej informacji na temat używania tych identyfikatorów, zobacz Instalowanie strony [programu Visual Studio 2017 za pomocą parametrów wiersza polecenia.](use-command-line-parameters-to-install-visual-studio.md) Aby uzyskać listę identyfikatorów obciążenia i składników dla innych produktów, zobacz stronę [Obciążenia i identyfikatory składników programu Visual Studio 2017.](workload-and-component-ids.md)

## <a name="test-professional"></a>Test Professional

**Identyfikator:** Microsoft.VisualStudio.Workload.TestProfessional

**Opis:** Test Professional oferuje zintegrowane narzędzia testujące skierowane do testerów ogólnych, które pomagają im zwiększyć ich potrzeby w zakresie testowania w całym cyklu życia testowania.

### <a name="components-included-by-this-workload"></a>Składniki objęte tym obciążeniem

Identyfikator składnika | Nazwa | Wersja | Typ zależności
--- | --- | --- | ---
Microsoft.VisualStudio.Component.TestTools.FeedbackClient | Microsoft Feedback Client | 15.6.27406.0 | Wymagany
Microsoft.VisualStudio.Component.TestTools.MicrosoftTestManager | Microsoft Test Manager | 15.6.27406.0 | Wymagany

## <a name="unaffiliated-components"></a>Składniki niepowiązane

Są to składniki, które nie są dołączone do żadnego obciążenia, ale mogą być wybrane jako pojedynczy składnik.

Identyfikator składnika | Nazwa | Wersja
--- | --- | ---
Nie dotyczy | Nie dotyczy | Nie dotyczy

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Identyfikatory obciążeń i składników programu Visual Studio](workload-and-component-ids.md)
* [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Tworzenie instalacji w trybie offline programu Visual Studio](create-an-offline-installation-of-visual-studio.md)
