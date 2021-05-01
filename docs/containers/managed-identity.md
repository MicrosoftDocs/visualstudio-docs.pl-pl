---
title: Jak używać tożsamości zarządzanej z Bridge to Kubernetes
ms.technology: vs-azure
ms.date: 04/28/2021
ms.topic: conceptual
description: Dowiedz się, jak używać tożsamości zarządzanej Azure Active Directory (Azure AD) w klastrze usługi AKS przy użyciu Bridge to Kubernetes
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: e4847b25531b48c8200a2620ca3e975f9677c881
ms.sourcegitcommit: 60b7a6159045a44293043a519c8ea6d915bf2c31
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/01/2021
ms.locfileid: "108335092"
---
# <a name="use-managed-identity-with-bridge-to-kubernetes"></a>Używanie tożsamości zarządzanej z Bridge to Kubernetes

Jeśli klaster usługi [](/azure/active-directory/managed-identities-azure-resources/overview) AKS używa funkcji zabezpieczeń tożsamości zarządzanej do zabezpieczania dostępu do wpisów tajnych i zasobów, Bridge to Kubernetes wymaga specjalnej konfiguracji, aby zapewnić możliwość pracy z tymi funkcjami. Token Azure Active Directory (AD) musi zostać pobrany na komputer lokalny, aby upewnić się, że lokalne wykonywanie i debugowanie jest prawidłowo zabezpieczone i wymaga to specjalnej konfiguracji w Bridge to Kubernetes. W tym artykule pokazano, jak skonfigurować Bridge to Kubernetes do pracy z usługami, które korzystają z tożsamości zarządzanej.

## <a name="how-to-configure-your-service-to-use-managed-identity"></a>Jak skonfigurować usługę do używania tożsamości zarządzanej

Aby włączyć maszynę lokalną z obsługą tożsamości zarządzanej, w pliku *KubernetesLocalConfig.yaml* w `enableFeatures` sekcji dodaj . `ManagedIdentity` Dodaj `enableFeatures` sekcję , jeśli jeszcze jej tam nie ma.

```yaml
enableFeatures:
    ManagedIdentity
```

> [!WARNING]
> Pamiętaj, aby używać tożsamości zarządzanej tylko dla usługi Bridge to Kubernetes podczas pracy z klastrami dewelopera, a nie klastrami produkcyjnymi, ponieważ token usługi Azure AD jest pobierany na komputer lokalny, co stanowi potencjalne zagrożenie bezpieczeństwa.

Jeśli nie masz pliku *KubernetesLocalConfig.yaml,* możesz go utworzyć. Zobacz [How to: Configure Bridge to Kubernetes (3.0: konfigurowanie Bridge to Kubernetes).](configure-bridge-to-kubernetes.md)

## <a name="how-to-fetch-the-azure-active-directory-tokens"></a>Jak pobrać tokeny Azure Active Directory tokeny

Podczas pobierania tokenu musisz upewnić się, że korzystasz z kodu lub <xref:Azure.Identity.DefaultAzureCredential> <xref:Azure.Identity.ManagedIdentityCredential> .

Poniższy kod w języku C# pokazuje, jak pobrać poświadczenia konta magazynu w przypadku korzystania z programu `ManagedIdentityCredential` :

```csharp
var credential = new ManagedIdentityCredential(miClientId);
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

Poniższy kod pokazuje, jak pobrać poświadczenia konta magazynu w przypadku użycia wartości DefaultAzureCredential:

```csharp
var credential = new DefaultAzureCredential();
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

Aby dowiedzieć się, jak uzyskać dostęp do innych zasobów platformy Azure przy użyciu tożsamości zarządzanej, zobacz [sekcję Następne](#next-steps) kroki.

## <a name="receive-azure-alerts-when-tokens-are-downloaded"></a>Otrzymywanie alertów platformy Azure po pobraniu tokenów

Zawsze, gdy Bridge to Kubernetes w usłudze, token usługi Azure AD jest pobierany na komputer lokalny. W takim przypadku możesz włączyć alerty platformy Azure, aby były powiadamiane. Aby uzyskać więcej informacji, zobacz [Włączanie Azure Defender](/azure/security-center/enable-azure-defender). Należy pamiętać, że istnieje opłata (po 30-dniowym okresie próbnym).

## <a name="next-steps"></a>Następne kroki

Teraz, po skonfigurowaniu usługi Bridge to Kubernetes do pracy z klastrem usługi AKS, który używa tożsamości zarządzanej, możesz debugować w zwykły sposób. Zobacz [bridge-to-kubernetes.md#connect-to-your-cluster-and-debug-a-service].

Dowiedz się więcej na temat używania tożsamości zarządzanej do uzyskiwania dostępu do zasobów platformy Azure, korzystając z następujących samouczków:

- [Samouczek: używanie przypisanej przez system tożsamości zarządzanej maszyny wirtualnej z systemem Linux do uzyskiwania dostępu do usługi Azure Storage](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-storage)
- [Samouczek: używanie przypisanej przez system tożsamości zarządzanej na maszynie wirtualnej z systemem Linux do uzyskiwania dostępu do usługi Azure Data Lake Store](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-datalake)
- [Samouczek: używanie przypisanej przez system tożsamości zarządzanej maszyny wirtualnej z systemem Linux do uzyskiwania dostępu do usługi Azure Key Vault](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-nonaad)

W tej sekcji znajdują się również inne samouczki dotyczące używania tożsamości zarządzanej do uzyskiwania dostępu do innych zasobów platformy Azure.

## <a name="see-also"></a>Zobacz też

[Azure Active Directory](/azure/active-directory/managed-identities-azure-resources/)
