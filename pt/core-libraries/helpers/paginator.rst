
PaginatorHelper
###############

.. php:class:: PaginatorHelper(View $view, array $settings = array())

O Pagination é usado para mostrar os controles de paginação, como por exemplo, os números de páginas e links de próximo/anterior. Funciona junto com o
:php:class:`PaginatorComponent`.

Veja também :doc:`/core-libraries/components/pagination` para mais informações sobre como
criar conjuntos de dados paginados e como fazer consultas paginadas.

Criando links de ordenação
===================

.. php:method:: sort($key, $title = null, $options = array())

    :param string $key: O nome da chave do conjunto de dados a ser ordenado
    :param string $title: Título do link. Se $title for nulo, $key será
        usada como título e será gerada por inflexão.
    :param array $options: Opções para o link de ordenação.

Gera um link de ordenação. Configura parametros nomeados ou de consulta para a ordenação e 
direção. Links serão ordenados ASC por padrão. Após o primeiro click, links
generados com ``sort()`` terão a troca de direção automática. A ordenação padrão do link é 'asc'. 
Se o resultset estiver configurado 'asc' pela chave especificada
o link retornado estará em 'desc'.

Chaves aceitas para ``$options``:

* ``escape`` Se você quer que o conteúdo HTML seja codificado em entidades. Sim, por padrão.
* ``model`` O model a ser usado, padrão :php:meth:`PaginatorHelper::defaultModel()`.
* ``direction`` A direção padrão a ser utilizada quando o link não está ativo.
* ``lock`` direção de bloqueio. Só vai usar a direção padrão, então, falso.

  .. versionadded:: 2.5
    Agora você pode configurar a opção lock para true para travar a direção de ordenação para a especificada.

Assumindo que você está paginando alguns posts que estão na página um::

    echo $this->Paginator->sort('user_id');

Saída:

.. code-block:: html

    <a href="/posts/index/page:1/sort:user_id/direction:asc/">User Id</a>

Você pode usar o parâmetro título para criar um texto personalizado para seu link::

    echo $this->Paginator->sort('user_id', 'User account');

Saída:

.. code-block:: html

    <a href="/posts/index/page:1/sort:user_id/direction:asc/">User account</a>

Se você está usando HTML, como imagens, nos seus links, lembre-se de colocar escaping off::

    echo $this->Paginator->sort(
      'user_id',
      '<em>User account</em>',
      array('escape' => false)
    );

Saída:

.. code-block:: html

    <a href="/posts/index/page:1/sort:user_id/direction:asc/">
      <em>User account</em>
    </a>

A opção direção pode ser usada para configurar a direção padrão para um link. Uma vez que
o link for ativado, Ele vai normalmente trocar as direções::

    echo $this->Paginator->sort('user_id', null, array('direction' => 'desc'));

Saída:

.. code-block:: html

    <a href="/posts/index/page:1/sort:user_id/direction:desc/">User Id</a>

A opção lock pode ser usada para travar a ordenação  sorting na direção especificada::

    echo $this->Paginator->sort('user_id', null, array('direction' => 'asc', 'lock' => true));

.. php:method:: sortDir(string $model = null, mixed $options = array())

    Pega a direção atual na qual os dados estão ordenados.

.. php:method:: sortKey(string $model = null, mixed $options = array())

    Pega a chave atual pela qual os dados estão ordenados.

Criando links de números de página
==========================


Paginator
#########

.. php:class:: PaginatorHelper(View $view, array $settings = array())

.. note::
    A documentação não é atualmente suportada pela lingua portuguesa nesta
    página.

    Por favor, sinta-se a vontade para nos enviar um pull request no
    `Github <https://github.com/cakephp/docs>`_ ou use o botão
    **Improve This Doc** para propor suas mudanças diretamente.

    Você pode referenciar-se à versão inglesa no menu de seleção superior
    para obter informações sobre o tópico desta página.

.. meta::
    :title lang=pt: PaginatorHelper
    :description lang=pt: The Pagination helper is used to output pagination controls such as page numbers and next/previous links.
    :keywords lang=pt: paginator helper,pagination,sort,page number links,pagination in views,prev link,next link,last link,first link,page counter
