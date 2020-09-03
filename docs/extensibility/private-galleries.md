---
title: Galerie prywatne | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444651"
---
# <a name="private-galleries"></a>Galerie prywatne
Możesz udostępniać kontrolki, szablony i narzędzia, które tworzysz, publikując je w *prywatnej galerii* w intranecie w organizacji, w następujący sposób:

- Utwórz źródło danych Atom (RSS) do odpowiednio skonfigurowanej lokalizacji centralnej (repozytorium) w intranecie. Aby uzyskać więcej informacji, zobacz [How to: Create a Atom paszowy for a Private Gallery](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

- Rozpowszechnij plik *. pkgdef* , który opisuje galerię prywatną. Zalecamy tę konfigurację dla administratorów, którzy chcą łączyć galerię prywatną z wieloma komputerami w tym samym czasie.

## <a name="add-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Dodawanie prywatnej galerii do rozszerzeń i aktualizacji w programie Visual Studio
 Gdy dostępna jest Galeria prywatna, można ją dodać do **rozszerzeń i aktualizacji** w programie Visual Studio.

 ![Okno dialogowe dodawania Menedżera rozszerzeń](../extensibility/media/em_adddialog.png "EM_AddDialog")

### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Aby dodać galerię prywatną do rozszerzeń i aktualizacji

1. Na pasku menu wybierz **Narzędzia**  >  **Opcje**.

2. W węźle **środowisko** wybierz pozycję **rozszerzenia i aktualizacje**.

3. Wybierz przycisk **Dodaj**.

4. W polu **Nazwa** wprowadź nazwę galerii prywatnej, na przykład `My Gallery` .

5. W polu **adres URL** wprowadź adres URL źródła danych Atom lub witryny programu SharePoint, która obsługuje galerię prywatną.

    1. Jeśli host jest strumieniowym źródłem Atom, który nawiązuje połączenie z galerią prywatną, adres URL będzie wyglądać następująco: `http://www.mywebsite/mygallery/atom.xml` .  Ten adres URL może odwoływać się do pliku lub ścieżki sieciowej.

    2. Jeśli host jest witryną programu SharePoint, adres URL będzie wyglądać następująco: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` .

### <a name="manage-private-galleries"></a>Zarządzaj prywatnymi galeriami
 Administrator może udostępnić prywatną galerię wielu komputerom w tym samym czasie, modyfikując rejestr systemu na każdym komputerze. Aby to osiągnąć, Utwórz plik *. pkgdef* , który opisuje nowe klucze rejestru i ich wartości.  Ten plik ma następujący format.

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

 Aby uzyskać więcej informacji, zobacz [How to: Manage a Private Gallery przy użyciu ustawień rejestru](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).

## <a name="install-extensions-from-a-private-gallery"></a>Instalowanie rozszerzeń z galerii prywatnej
 Rozszerzenia programu Visual Studio można wyszukiwać i instalować z galerii prywatnej w obszarze **rozszerzenia i aktualizacje**. W poniższych krokach użyto prywatnej galerii o nazwie `My Gallery` .

 ![Menedżer rozszerzeń instalujący prywatną galerię](../extensibility/media/em_.png "EM_")

### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Aby wyszukać i zainstalować rozszerzenia z galerii prywatnej

1. Na pasku menu wybierz kolejno opcje **Narzędzia**  >  **rozszerzenia i aktualizacje**.

2. W lewym okienku wybierz pozycję **rozszerzenia online**, a następnie wybierz pozycję **Moja Galeria**.

3. W okienku po prawej stronie Wybierz rozszerzenie, a następnie wybierz przycisk **Pobierz** .

## <a name="update-extensions-from-a-private-gallery"></a>Aktualizowanie rozszerzeń z galerii prywatnej
 W przypadku opublikowania nowych wersji rozszerzeń programu Visual Studio w prywatnej galerii można zaktualizować zainstalowane rozszerzenia. W poniższych krokach użyto prywatnej galerii o nazwie `My Repository` .

 ![Aktualizacja galerii prywatnych programu Extension Manager](../extensibility/media/em_update.png "EM_Update")

### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Aby zaktualizować zainstalowane rozszerzenie z galerii prywatnej

1. Na pasku menu wybierz kolejno opcje **Narzędzia**  >  **rozszerzenia i aktualizacje**.

2. W lewym okienku wybierz pozycję **aktualizacje**, a następnie wybierz pozycję **moje repozytorium**.

3. W okienku po prawej stronie Wybierz rozszerzenie, a następnie kliknij przycisk **Aktualizuj** .

## <a name="see-also"></a>Zobacz też
- [Znajdowanie i używanie rozszerzeń programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
- [Wyślij rozszerzenia programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
