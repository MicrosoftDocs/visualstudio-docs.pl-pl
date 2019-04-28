---
title: Wprowadzenie czcionkę i kolor informacje dotyczące kolorowania tekstu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f03b23076b1eea203166bb0322f05927480a278
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417171"
---
# <a name="get-font-and-color-information-for-text-colorization"></a>Uzyskaj informacje czcionek i kolorów tekstu kolorowania
Proces, który renderuje lub wyświetla wyróżnione kolorem tekstu w elementach interfejsu użytkownika zależy od typu projektu, jego technologii i dla deweloperów preferencji. **Czcionki i kolory** strona właściwości są przechowywane ustawienia.

 Większość implementacji, które są wyświetlane wyróżnione kolorem tekstu muszą <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> i skojarzone interfejsy, dla ustawienia wyświetlania prezentacji, pobieranie i przechowywanie tekstu.

> [!NOTE]
> Podczas dostosowywania podstawowy edytor (który obsługuje **EditorCategory tekstu**), zaleca się używać technologii kolorowanie usługi języka. Aby uzyskać więcej informacji, zobacz [Przegląd czcionek i kolorów](../extensibility/font-and-color-overview.md).

## <a name="get-default-font-and-color-information"></a>Uzyskaj informacje czcionkę i kolor domyślny
 Wszystkie **czcionki i kolory** należy określić ustawienia okna wyświetlania tekstu w **Wyświetle elementy** jednego **kategorii**. Aby uzyskać więcej informacji, zobacz [czcionki i kolory, środowisko, okno dialogowe Opcje](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

Kolorować, pakietu VSPackage musi uzyskać bieżące **czcionki i kolory** ustawienia. Pakietu VSPackage mogą uzyskać bieżące ustawienia w następujący sposób, w zależności od jego potrzeb:

- Użyj mechanizmu stanu trwałego czcionek i kolorów do pobrania przechowywanych lub bieżącego stanu. Aby uzyskać więcej informacji, zobacz [dostępu przechowywane ustawienia czcionek i kolorów](../extensibility/accessing-stored-font-and-color-settings.md).

- Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfejsu usługi, która udostępnia dane czcionek i kolorów, aby pobrać wystąpienie obiektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, jeśli pakietu VSPackage nie jest również dostawcy czcionek i kolorów.

- Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interfejsu.

Aby upewnić się, że wyniki uzyskane za pomocą sondowania znajdują się w górę do daty, warto użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfejs do określenia, czy aktualizacja jest wymagana przed wywołaniem metody pobierania <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu.

Po użytkownik uzyskał informacje czcionek i kolorów, tekst, który ma być wyświetlany w celu oznaczenia elementów, które wymagają kolorowanie przeanalizować. Wyświetlanie tekstu w oknie przy użyciu odpowiednich czcionek i kolorów.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [Użyj czcionek i tekstu](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [Praca z kolorami](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI (graficzny interfejs urządzenia)](https://msdn.microsoft.com/library/7e1d4540-bb2e-4257-8eee-eee376acba83)