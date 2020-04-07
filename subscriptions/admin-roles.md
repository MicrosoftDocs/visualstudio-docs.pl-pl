---
title: Role superadministratorów i administratorów w portalu administracyjnym
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 04/07/2020
ms.topic: conceptual
description: Dowiedz się więcej o rolach superadministratora i administratora oraz o przypisywaniu administratorów.
ms.openlocfilehash: 234153dcb8dd06b33ab7aac78e587439684963f9
ms.sourcegitcommit: 1f7aed335c48215dff5c151f76f22e3f10e8b564
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80808372"
---
# <a name="super-admins-and-administrators-for-visual-studio-subscription-agreements"></a>Super administratorzy i administratorzy umów subskrypcji programu Visual Studio

Istnieją dwie różne role w nowym portalu administracyjnym subskrypcji programu Visual Studio dla klientów licencjonowania zbiorowego. Te role są podobne do roli Kontakt podstawowy/powiadomienia i rola Menedżera subskrypcji, które istniały w VLSC.

**Super admini:** Gdy organizacja jest początkowo skonfigurowana, kontakt podstawowy lub kontakt z powiadomieniami staje się domyślnie superadministratorem. Kontakt podstawowy lub Kontakt z powiadomieniami może wybrać przypisanie dodatkowych superadministratorów lub administratorów. Superadministrator może dodawać i usuwać innych administratorów, a także subskrybentów. Jeśli w systemie jest więcej niż dwóch superadministratorów, superadministrator może usunąć wszystkie z wyjątkiem dwóch ostatnich ze względów bezpieczeństwa.

**Administratorzy:** Administratora może przypisać tylko superadministrator. Administrator może zarządzać subskrybentami tylko w umowach przypisywanych im przez superadministratora.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-administrators"></a>Przypisywanie administratorów
Aby przypisać nowych administratorów (administratorów):
1. Zaloguj się https://manage.visualstudio.com przy użyciu adresu e-mail przypisanego jako superadministrator w umowie, za pośrednictwem której zakupiono subskrypcje.
2. Kliknij kartę z **etykietą Zarządzaj administratorami**.
3. Kliknij przycisk **Dodaj**.
   > [!div class="mx-imgBorder"]
   > ![Dodawanie administratorów](_img/admin-roles/add-admins.png)
4. Wypełnij formularz informacjami o nowym administratorze.  
   > [!div class="mx-imgBorder"]
   > ![Dodawanie formularza administratora](_img/admin-roles/add-form.png)

   > [!NOTE]
   > Jeśli chcesz, aby ten administrator mógł przypisać dodatkowych administratorów, pamiętaj, aby zaznaczyć pole **Superadministrator.**

5. Po **kliknięciu przycisku Dodaj,** aby przypisać nowego administratora, otrzymają oni wiadomość e-mail z zaproszeniem do zalogowania się do portalu.  

## <a name="resources"></a>Zasoby
- [Pomoc techniczna dotycząca subskrypcji programu Visual Studio i administrowania nim](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Następne kroki
- Dowiedz się, jak [przypisać subskrypcje](assign-license.md)
- Dowiedz się więcej o pełnym zakresie [korzyści subskrypcyjnych](https://visualstudio.microsoft.com/vs/benefits/)
- [Ustawianie preferencji umowy](admin-prefs.md) 


