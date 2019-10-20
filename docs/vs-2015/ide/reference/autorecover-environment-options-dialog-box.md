---
title: Autoodzyskiwanie, środowisko, Opcje — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 743543e03806a842eabc2bbfc69011d63b1264d0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660966"
---
# <a name="autorecover-environment-options-dialog-box"></a>AutoRecover, środowisko, opcje — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Za pomocą tej strony okna dialogowego Opcje można określić, czy kopie zapasowe plików mają być tworzone automatycznie. Ta strona umożliwia również określenie, czy zmodyfikowane pliki są przywracane, gdy zintegrowane środowisko programistyczne (IDE) jest nieoczekiwanie zamykane. Możesz uzyskać dostęp do tego okna dialogowego, wybierając menu **Narzędzia** i wybierając pozycję **Opcje**, a następnie wybierając folder **środowisko** i wybierając stronę **Autoodzyskiwanie** . Jeśli ta strona nie jest wyświetlana na liście, wybierz pozycję **Pokaż wszystkie ustawienia** w oknie dialogowym **Opcje** .

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **Zapisuj informacje Autoodzyskiwania co \<n > minut** Użyj tej opcji, aby dostosować częstotliwość automatycznego zapisywania pliku w edytorze. W przypadku wcześniej zapisanych plików kopia pliku jest zapisywana w \\. ..\My Documents\Visual Studio \<*wersja*> \Backup \\ <*ProjectName*>. Jeśli plik jest nowy i nie został ręcznie zapisany, plik zostanie automatycznie zapisany przy użyciu losowo wygenerowanej nazwy pliku.

 **Zachowaj informacje automatycznego odzyskiwania dla \<n > dni** Użyj tej opcji, aby określić, jak długo program Visual Studio ma nadal tworzyć pliki do odzyskania.

## <a name="see-also"></a>Zobacz też
 [Opcje, okno dialogowe](../../ide/reference/options-dialog-box-visual-studio.md)
