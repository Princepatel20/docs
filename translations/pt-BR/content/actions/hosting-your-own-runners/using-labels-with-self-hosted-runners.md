---
title: Usar etiquetas com executores auto-hospedados
intro: Você pode usar etiquetas para organizar os seus executores auto-hospedados com base em suas características.
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
type: tutorial
shortTitle: Executores de etiqueta
---

{% data reusables.actions.ae-self-hosted-runners-notice %}
{% data reusables.actions.enterprise-beta %}
{% data reusables.actions.enterprise-github-hosted-runners %}

Para obter informações sobre como usar etiquetas para encaminhar trabalhos para tipos específicos de executores auto-hospedados, consulte "[Usando executores auto-hospedados em um fluxo de trabalho](/actions/hosting-your-own-runners/using-self-hosted-runners-in-a-workflow)."

{% data reusables.actions.self-hosted-runner-management-permissions-required %}

## Criar etiquetas personalizadas

{% ifversion fpt or ghec or ghes > 3.3 or ghae-issue-5091 %}
{% data reusables.actions.self-hosted-runner-navigate-to-repo-org-enterprise %}
 {% data reusables.actions.settings-sidebar-actions-runner-selection %}
 1. Na seção "Etiquetas", clique em {% octicon "gear" aria-label="The Gear icon" %}.
 1. No campo "Encontrar ou criar uma etiqueta", digite o nome da sua nova etiqueta e clique em **Criar nova etiqueta**. O rótulo personalizado é criado e atribuído ao executor auto-hospedado. É possível remover as etiquetas personalizadas dos executores auto-hospedados, mas não é possível excluí-las manualmente. {% data reusables.actions.actions-unused-labels %}
{% elsif ghae or ghes < 3.4 %}
{% data reusables.actions.self-hosted-runner-navigate-to-repo-org-enterprise %}
{% data reusables.actions.self-hosted-runner-list %}
{% data reusables.actions.self-hosted-runner-list-group %}
{% data reusables.actions.self-hosted-runner-labels-view-assigned-labels %}
1. No campo "Filtrar etiquetas", digite o nome da sua nova etiqueta e clique em **Criar nova etiqueta**. ![Adicionar etiqueta do executor](/assets/images/help/settings/actions-add-runner-label.png)

O rótulo personalizado é criado e atribuído ao executor auto-hospedado. É possível remover as etiquetas personalizadas dos executores auto-hospedados, mas não é possível excluí-las manualmente. {% data reusables.actions.actions-unused-labels %}
{% endif %}

## Atribuir uma etiqueta a um executor auto-hospedado

{% ifversion fpt or ghec or ghes > 3.3 or ghae-issue-5091 %}
{% data reusables.actions.self-hosted-runner-navigate-to-repo-org-enterprise %}
{% data reusables.actions.settings-sidebar-actions-runner-selection %}
{% data reusables.actions.runner-label-settings %}
  1. Para atribuir uma etiqueta ao executor auto-hospedado, no campo "Localizar ou criar uma etiqueta", clique na etiqueta.
{% elsif ghae or ghes < 3.4 %}
{% data reusables.actions.self-hosted-runner-navigate-to-repo-org-enterprise %}
{% data reusables.actions.self-hosted-runner-list %}
{% data reusables.actions.self-hosted-runner-list-group %}
{% data reusables.actions.self-hosted-runner-labels-view-assigned-labels %}
1. Clique em uma etiqueta a ser atribuída ao seu executor auto-hospedado.
{% endif %}

## Remover uma etiqueta personalizada de um executor auto-hospedado

{% ifversion fpt or ghec or ghes > 3.3 or ghae-issue-5091 %}
{% data reusables.actions.self-hosted-runner-navigate-to-repo-org-enterprise %}
{% data reusables.actions.settings-sidebar-actions-runner-selection %}
{% data reusables.actions.runner-label-settings %}
  1. No campo "Encontre ou crie uma etiqueta", as etiquetas atribuídas são marcadas com a
Ícone de {% octicon "check" aria-label="The Check icon" %}. Clique em uma etiqueta marcada para cancelar a atribuição do seu executor auto-hospedado.
{% elsif ghae or ghes < 3.4 %}
{% data reusables.actions.self-hosted-runner-navigate-to-repo-org-enterprise %}
{% data reusables.actions.self-hosted-runner-list %}
{% data reusables.actions.self-hosted-runner-list-group %}
{% data reusables.actions.self-hosted-runner-labels-view-assigned-labels %}
1. Clique na etiqueta atribuída para removê-la do seu executor auto-hospedado. {% data reusables.actions.actions-unused-labels %}
{% endif %}

## Usar o script de configuração para criar e atribuir rótulos

Você pode usar o script de configuração no executor auto-hospedado para criar e atribuir etiquetas personalizadas. Por exemplo, este comando atribui ao executor auto-hospedado uma etiqueta denominada `gpu`.

```shell
./config.sh --labels gpu
```

Caso não exista, a etiqueta será criada. Você também pode usar esta abordagem para atribuir as etiquetas-padrão a executores, como `x64` ou `linux`. Quando as etiquetas-padrão são atribuídas usando o script de configuração, {% data variables.product.prodname_actions %} aceita-as como dadas e não valida que o executor está realmente usando esse sistema operacional ou arquitetura.

Você pode usar a separação por vírgula para atribuir múltiplas etiquetas. Por exemplo:

```shell
./config.sh --labels gpu,x64,linux
```

{% note %}

** Observação:** Se você substituir um executor existente, você deverá reatribuir quaisquer etiquetas personalizadas.

{% endnote %}
