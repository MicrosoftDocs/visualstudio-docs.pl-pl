---
title: Strona zabezpieczeń, Projektant projektu
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1834713ad114ab8a86e314bbe052f4873b308956
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593580"
---
# <a name="security-page-project-designer"></a>Strona zabezpieczeń, Projektant projektu

Strona **Zabezpieczenia** **projektanta projektu** służy do konfigurowania ustawień zabezpieczeń dostępu do kodu dla aplikacji, które są wdrażane przy użyciu wdrożenia ClickOnce. Aby uzyskać więcej informacji, zobacz [Zabezpieczenia dostępu do kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

Aby uzyskać dostęp do strony **Zabezpieczenia,** kliknij węzeł projektu w **Eksploratorze rozwiązań,** a następnie w menu **Projekt** kliknij polecenie **Właściwości**. Po wyświetleniu **projektanta projektu** kliknij kartę **Zabezpieczenia.**

## <a name="security-settings"></a>Ustawienia zabezpieczeń

 **Włącz ustawienia zabezpieczeń ClickOnce**

Określa, czy ustawienia zabezpieczeń są włączone w czasie projektowania. Gdy ta opcja jest wyczyszczona, wszystkie inne opcje na stronie **Zabezpieczenia** są niedostępne.

> [!NOTE]
> Podczas publikowania aplikacji za pomocą kreatora **publikowania** ta opcja jest automatycznie włączana.

Po wybraniu tej opcji można wybrać jeden z dwóch przycisków radiowych: **Jest to aplikacja pełnego zaufania** lub Jest to aplikacja **częściowego zaufania**.

Domyślnie w przypadku projektów aplikacji przeglądarki sieci Web WPF ta opcja jest zaznaczona.

Domyślnie dla wszystkich innych typów projektów ta opcja jest wyczyszczona.

 **Jest to aplikacja pełnego zaufania**

Jeśli wybierzesz tę opcję, aplikacja zażąda uprawnień pełnego zaufania, gdy jest zainstalowana lub uruchamiana na komputerze klienckim. Należy unikać korzystania z pełnego zaufania, jeśli to możliwe, ponieważ aplikacja zostanie przyznany nieograniczony dostęp do zasobów, takich jak system plików i rejestru.

Domyślnie w przypadku projektów aplikacji przeglądarki sieci Web WPF ta opcja jest ustawiona na częściowe zaufanie.

Domyślnie dla wszystkich innych typów projektów ta opcja jest ustawiona na Pełne zaufanie.

 **Jest to aplikacja częściowego zaufania**

Jeśli wybierzesz tę opcję, aplikacja zażąda uprawnień częściowego zaufania, gdy jest zainstalowana lub uruchamiana na komputerze klienckim. *Częściowe zaufanie* oznacza, że będą uruchamiane tylko akcje, które są dozwolone w ramach wymaganych uprawnień zabezpieczeń dostępu do kodu. Aby uzyskać więcej informacji na temat konfigurowania uprawnień zabezpieczeń, zobacz [Zabezpieczenia dostępu do kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

Ustawienia zabezpieczeń częściowego zaufania można określić, konfigurując opcje w obszarze **Uprawnienia zabezpieczeń Po kliknięciu.**

## <a name="clickonce-security-permissions"></a>Kliknięciezacedy zabezpieczeńonce

 **Strefa, w, z**

Określa domyślny zestaw uprawnień zabezpieczeń dostępu do kodu. Wybierz **pozycję Internet** lub Lokalny **intranet** dla ograniczonego zestawu uprawnień lub wybierz opcję **(Niestandardowy),** aby skonfigurować niestandardowy zestaw uprawnień. Jeśli aplikacja żąda więcej uprawnień niż przyznane w strefie, ClickOnce zaufania monit pojawia się dla użytkownika końcowego, aby udzielić dodatkowych uprawnień. Aby uzyskać więcej informacji na temat konfigurowania uprawnień zabezpieczeń, zobacz [Zabezpieczenia dostępu do kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

Domyślnie w przypadku projektów aplikacji przeglądarki sieci Web WPF ta opcja jest ustawiona na **Internet**.

 **Edytuj uprawnienia XML**

Otwiera szablon manifestu aplikacji (app.manifest), aby skonfigurować uprawnienia dla **(niestandardowego)** zestawu uprawnień.

 **Zaawansowane**

Otwiera [okno dialogowe Zaawansowane ustawienia zabezpieczeń,](../../ide/reference/advanced-security-settings-dialog-box.md)które służy do konfigurowania ustawień debugowania aplikacji z ograniczonymi uprawnieniami. Te ustawienia są sprawdzane podczas debugowania, a wyjątki uprawnień wskazują, że aplikacja może potrzebować więcej uprawnień niż zdefiniowane w strefie.

## <a name="see-also"></a>Zobacz też

- <xref:System.Security.Permissions.WebBrowserPermission>
- <xref:System.Security.Permissions.MediaPermission>
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md)
- [Instrukcje: włączenie ustawień zabezpieczeń technologii ClickOnce](../../deployment/how-to-enable-clickonce-security-settings.md)
- [Porady: ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Instrukcje: ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Porady: debugowanie aplikacji ClickOnce przy użyciu ograniczonych uprawnień](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Kliknijonce zabezpieczenia i wdrażanie](../../deployment/clickonce-security-and-deployment.md)
- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Zaawansowane ustawienia zabezpieczeń — Okno dialogowe](../../ide/reference/advanced-security-settings-dialog-box.md)
