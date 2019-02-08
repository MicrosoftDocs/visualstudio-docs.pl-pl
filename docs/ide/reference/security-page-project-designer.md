---
title: Strona zabezpieczeń, Projektant projektu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71411ed03906e13ae666a12a67fbdb499d737b5f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936138"
---
# <a name="security-page-project-designer"></a>Strona zabezpieczeń, Projektant projektu

**Zabezpieczeń** strony **projektanta projektu** służy do konfigurowania ustawień zabezpieczeń dostępu kodu dla aplikacji, które są wdrażane przy użyciu [!INCLUDE[ndptecclick](../../deployment/includes/ndptecclick_md.md)] wdrożenia. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Aby uzyskać dostęp do **zabezpieczeń** kliknij węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **właściwości**. Podczas **projektanta projektu** zostanie wyświetlona, kliknij przycisk **zabezpieczeń** kartę.

## <a name="security-settings"></a>Ustawienia zabezpieczeń

 **Włączenie ustawień zabezpieczeń technologii ClickOnce**

 Określa, czy ustawienia zabezpieczeń są włączone w czasie projektowania. Jeśli ta opcja jest wyczyszczone, wszystkie inne opcje na **zabezpieczeń** strony są niedostępne.

> [!NOTE]
> Po opublikowaniu aplikacji za pomocą **Publikuj** kreatora, ta opcja jest automatycznie włączona.


 Po wybraniu tej opcji, użytkownik może wybrać jedną z dwóch przycisków radiowych: **Jest to aplikacja w trybie pełnego zaufania** lub **to częściowo zaufanych aplikacji**.

 Domyślnie projektów aplikacji przeglądarki sieci Web programu WPF ta opcja jest zaznaczona.

 Domyślnie dla wszystkich innych typów projektów ta opcja jest zaznaczona.

 **Jest to aplikacja w trybie pełnego zaufania**

 Jeśli wybierzesz tę opcję, aplikacja żąda uprawnień pełnego zaufania, gdy jest on zainstalowany, lub uruchomić na komputerze klienckim. Należy unikać przy użyciu pełnego zaufania, jeśli jest to możliwe, ponieważ zostanie przyznany aplikacji nieograniczony dostęp do zasobów, takich jak system plików i rejestru.

 Domyślnie projektów aplikacji przeglądarki sieci Web programu WPF ta opcja jest równa częściowego zaufania.

 Domyślnie dla wszystkich innych typów projektów ta opcja jest ustawiona na pełne zaufanie.

 **Jest to aplikacja częściowej relacji zaufania**

 Jeśli wybierzesz tę opcję, aplikacja żąda uprawnień częściowego zaufania, gdy jest on zainstalowany, lub uruchomić na komputerze klienckim. *Częściowej relacji zaufania* oznacza, że będą uruchamiane tylko akcje, które są dozwolone w obszarze uprawnienia zabezpieczeń dostępu kodu żądanej. Aby uzyskać więcej informacji o sposobie konfigurowania uprawnień zabezpieczeń, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Możesz określić ustawienia zabezpieczeń częściowego zaufania, konfigurując opcje w **uprawnienia zabezpieczeń aplikacji ClickOnce** obszaru.

## <a name="clickonce-security-permissions"></a>Uprawnienia zabezpieczeń aplikacji ClickOnce

 **Strefy, w której aplikacja zostanie zainstalowana z**

 Określa domyślny zestaw uprawnień zabezpieczeń dostępu kodu. Wybierz **Internet** lub **lokalny Intranet** ograniczonych uprawnień zestawu, lub opcję **(niestandardowy)** Aby skonfigurować niestandardowe uprawnienia należy ustawić. Jeśli aplikacja żąda więcej uprawnień niż udzielone w strefie, użytkownikowi końcowemu udzielać dodatkowych uprawnień pojawia się monit o udzielenie zaufania ClickOnce. Aby uzyskać więcej informacji o sposobie konfigurowania uprawnień zabezpieczeń, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Domyślnie projektów aplikacji przeglądarki sieci Web programu WPF, ta opcja jest ustawiona na **Internet**.

 **Edytuj uprawnienia XML**

 Otwiera szablon manifestu aplikacji (app.manifest) Aby skonfigurować uprawnienia dla **(niestandardowy)** zestaw uprawnień.

 **Zaawansowane**

 Otwiera [okno dialogowe Zaawansowane ustawienia zabezpieczeń](../../ide/reference/advanced-security-settings-dialog-box.md), która umożliwia konfigurowanie ustawień na potrzeby debugowania aplikacji z ograniczonymi uprawnieniami. Te ustawienia są sprawdzane podczas debugowania, a uprawnienie wyjątki wskazują na to, że aplikacja może być konieczne więcej uprawnień niż zdefiniowana w strefie.

## <a name="see-also"></a>Zobacz też

- <xref:System.Security.Permissions.WebBrowserPermission>
- <xref:System.Security.Permissions.MediaPermission>
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md)
- [Instrukcje: Włączanie ustawień zabezpieczeń technologii ClickOnce](../../deployment/how-to-enable-clickonce-security-settings.md)
- [Instrukcje: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Instrukcje: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Instrukcje: Debugowanie aplikacji ClickOnce przy użyciu ograniczonych uprawnień](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](../../deployment/clickonce-security-and-deployment.md)
- [Odwołanie do właściwości projektu](../../ide/reference/project-properties-reference.md)
- [Zaawansowane ustawienia zabezpieczeń, okno dialogowe](../../ide/reference/advanced-security-settings-dialog-box.md)