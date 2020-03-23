---
title: Usuwanie przypisań subskrypcji w portalu administracyjnym subskrypcji programu Visual Studio | Dokumenty firmy Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Dowiedz się, jak administratorzy mogą usuwać przypisania subskrypcji
ms.openlocfilehash: 6ed64f5c05f77bea7f157eee9e29bbb05aa8730d
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "78263252"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Usuwanie przydziałów w subskrypcjach programu Visual Studio
Gdy subskrybent nie wymaga już subskrypcji programu Visual Studio, na przykład po opuszczeniu firmy, ukończeniu projektu lub przełączeniu się do nowej roli zadania, można usunąć ich subskrypcję i przypisać ją innej osobie. Należy pamiętać, że po ponownym przydzieleniu subskrypcji nie wszystkie korzyści dla subskrybentów zostaną zresetowane.  Nowy użytkownik będzie mógł ubiegać się o nieodebrane klucze i wyświetlać wcześniej odebrane klucze, ale limity oświadczeń **nie** są resetowane.  W przypadku organizacji, które mają umowy Enterprise Agreement (EA), wszelkie korzyści, które były używane przez pierwotnego użytkownika, takie jak szkolenie Pluralsight, zostaną zresetowane. 

## <a name="delete-a-subscription-assignment"></a>Usuwanie przypisania subskrypcji
1. Kliknij nazwę subskrybenta, którego chcesz usunąć. Aby wybrać wielu subskrybentów do usunięcia, możesz kliknąć okrąg po lewej stronie nazwy subskrybenta, aby wybrać każdy z nich.  Możesz też przytrzymać klawisz **CTRL** i kliknąć każdego subskrybenta, którego chcesz usunąć.  Naciśnij **klawisze CTRL + A,** aby wybrać i usunąć wszystkich subskrybentów. 
2. Aby usunąć zaznaczonych subskrybentów, kliknij przycisk **Usuń**.
3. Gdy pojawi się komunikat z prośbą o potwierdzenie usunięcia, kliknij przycisk **OK**.
   > [!div class="mx-imgBorder"]
   > ![Usuwanie subskrybentów](_img/delete-license/delete-subscribers.png)

   > [!NOTE]
   > Usuwanie zbiorcze przy użyciu szablonu jest niedostępne. W przypadku organizacji, które zarządzają przydziałami subskrypcji za pośrednictwem grup zabezpieczeń usługi Azure Active Directory, zobacz [nasz artykuł,](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) aby uzyskać więcej informacji na temat usuwania.  

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
- Chcesz zmienić subskrypcję bez jej usuwania?  Dowiedz się, jak [edytować subskrypcje](edit-license.md)
- Aby uzyskać pomoc dotyczącą znajdowania określonej subskrypcji, zapoznaj się z [wyszukaj subskrypcję](search-license.md).
- Chcesz utworzyć listę wszystkich subskrypcji?  Zobacz [Eksportowanie subskrypcji](exporting-subscriptions.md).


