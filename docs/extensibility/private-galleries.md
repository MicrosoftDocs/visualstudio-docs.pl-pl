---
title: Prywatne galerie | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: afd1d79d7f1846e60386d2a9478466bf7eae72e4
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444651"
---
# <a name="private-galleries"></a>Prywatne galerie
Formanty, szablony i narzędzia można udostępniać, publikując je w *prywatnej galerii* w intranecie dla organizacji w następujący sposób:

- Utwórz kanał informacyjny Atom (RSS) w odpowiednio skonfigurowanej centralnej lokalizacji (repozytorium) w intranecie. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie kanału informacyjnego Atom dla galerii prywatnej](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

- Rozesłaj plik *pkgdef* opisujący galerię prywatną. Zaleca się tę konfigurację dla administratorów, którzy chcą połączyć galerię prywatną z wieloma komputerami w tym samym czasie.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Dodawanie galerii prywatnej do rozszerzeń i aktualizacji w programie Visual Studio
 Gdy galeria prywatna jest dostępna, można dodać ją do **rozszerzeń i aktualizacji** w programie Visual Studio.

 ![Okno dialogowe Dodawanie menedżera rozszerzeń](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Aby dodać galerię prywatną do rozszerzeń i aktualizacji

1. Na pasku menu wybierz pozycję**Opcje** **narzędzi** > .

2. W węźle **Środowisko** wybierz pozycję **Rozszerzenia i aktualizacje**.

3. Wybierz przycisk **Dodaj**.

4. W polu **Nazwa** wprowadź na przykład nazwę galerii `My Gallery`prywatnej .

5. W polu **ADRES URL** wprowadź adres URL kanału informacyjnego Atom lub witryny programu SharePoint, w ramach których znajduje się galeria prywatna.

    1. Jeśli host jest kanałem informacyjnym Atom, który łączy się z `http://www.mywebsite/mygallery/atom.xml`galerią prywatną, adres URL będzie podobny do tego: .  Ten adres URL może odnosić się do pliku lub ścieżki sieciowej.

    2. Jeśli host jest witryną programu SharePoint, adres `http://mysharepoint/sites/mygallery/forms/AllItems.aspx`URL będzie podobny do następującego: .

### <a name="manage-private-galleries"></a>Zarządzanie prywatnymi galeriami
 Administrator może udostępnić prywatną galerię kilku komputerom jednocześnie, modyfikując rejestr systemowy na każdym komputerze. Aby to osiągnąć, należy utworzyć plik *pkgdef* opisujący nowe klucze rejestru i ich wartości.  Format tego pliku jest następujący.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Aby uzyskać więcej informacji, zobacz [Jak: Zarządzanie galerią prywatną przy użyciu ustawień rejestru](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Instalowanie rozszerzeń z galerii prywatnej
 Rozszerzenia programu Visual Studio można wyszukiwać i instalować z galerii prywatnej w **programie Rozszerzenia i aktualizacje**. W poniższych krokach `My Gallery`użyto galerii prywatnej o nazwie .

 ![Menedżer rozszerzeń Instalowanie galerii prywatnej](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Aby wyszukać i zainstalować rozszerzenia z galerii prywatnej

1. Na pasku menu wybierz pozycję**Rozszerzenia i aktualizacje** **narzędzi** > .

2. W lewym okienku wybierz pozycję **Rozszerzenia online**, a następnie wybierz pozycję **Moja galeria**.

3. W prawym okienku wybierz rozszerzenie, a następnie wybierz przycisk **Pobierz.**

## <a name="update-extensions-from-a-private-gallery"></a>Aktualizowanie rozszerzeń z galerii prywatnej
 Ponieważ nowe wersje rozszerzeń programu Visual Studio są publikowane w galerii prywatnej, można zaktualizować rozszerzenia, które zostały zainstalowane. W poniższych krokach `My Repository`użyto galerii prywatnej o nazwie .

 ![Aktualizacja prywatnej galerii menedżera rozszerzeń](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Aby zaktualizować zainstalowane rozszerzenie z galerii prywatnej

1. Na pasku menu wybierz pozycję**Rozszerzenia i aktualizacje** **narzędzi** > .

2. W lewym okienku wybierz pozycję **Aktualizacje**, a następnie wybierz pozycję **Moje repozytorium**.

3. W prawym okienku wybierz rozszerzenie, a następnie wybierz przycisk **Aktualizuj.**

## <a name="see-also"></a>Zobacz też
- [Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
- [Wysyłaj rozszerzenia programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
