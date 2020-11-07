---
title: Dostosuj domyślną stronę sieci Web dla aplikacji ClickOnce
description: Dowiedz się więcej o stronie sieci Web wygenerowanej podczas publikowania aplikacji ClickOnce w sieci Web, która zawiera nazwę aplikacji i inne informacje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbda4558622c2e244071a218d3d5e42196460113
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351209"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Instrukcje: dostosowywanie domyślnej strony sieci Web dla aplikacji ClickOnce
Podczas publikowania aplikacji ClickOnce w sieci Web strona sieci Web jest automatycznie generowana i publikowana razem z aplikacją. Strona domyślna zawiera nazwę aplikacji i linki do zainstalowania aplikacji, instalacji wymagań wstępnych lub uzyskania dostępu do pomocy w witrynie MSDN.

> [!NOTE]
> Rzeczywiste linki widoczne na stronie zależą od komputera, na którym strona jest wyświetlana i jakie są wymagania wstępne.

 Nazwa domyślna strony sieci Web jest *Publish.htm* ; można zmienić nazwę w **projektancie projektu**. Aby uzyskać więcej informacji, zobacz [How to: Określanie strony publikowania dla aplikacji ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 Strona sieci Web *Publish.htm* jest publikowana tylko w przypadku wykrycia nowszej wersji.

> [!NOTE]
> Zmiany wprowadzone w ustawieniach **publikowania** nie wpłyną na stronę *Publish.htm* , z wyjątkiem jednego wyjątku: Jeśli po wstępnym opublikowaniu zostaną dodane lub usunięte wymagania wstępne, lista wymagań wstępnych nie będzie już dokładna. Aby odzwierciedlić zmiany, należy zmodyfikować tekst linku wymagań wstępnych.

### <a name="to-customize-the-publish-web-page"></a>Aby dostosować stronę publikowania w sieci Web

1. Opublikuj aplikację ClickOnce w lokalizacji sieci Web. Aby uzyskać więcej informacji, zobacz [jak: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2. Na serwerze sieci Web otwórz plik *Publish.htm* w Visual Web Designer lub innym edytorze html.

3. Dostosuj stronę zgodnie z potrzebami i Zapisz ją.

4. Opcjonalny. Aby zapobiec zastąpieniu przez program Visual Studio dostosowanej strony publikowania w sieci Web, usuń zaznaczenie pola wyboru **automatycznie Generuj stronę sieci Web wdrożenia po każdej publikacji** w oknie dialogowym **Opcje publikacji** .

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Instrukcje: Określanie strony publikowania dla aplikacji ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)