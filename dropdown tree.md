>> 页面
```html
<div class="input-group-btn" id="div_indextype_tree">
                    <button type="button" class="btn btn-default dropdown-toggle" data-toggle="#" id="btn_showIndexTree">
                        选择
                        <span class="caret"></span>
                    </button>
                    <ul class="dropdown-menu pull-left">
                        <li>
                            <div class="row" style="margin:0;width: 200px;height: 300px;" id="tree_index_type_container">
                                <div id="tree_index_type"></div>
                            </div>
                        </li>
                    </ul>
                </div><!-- /btn-group -->
```

>> js
```javascript
$form.find('#btn_showIndexTree').on('click', function() {
      if ($form.find('#div_indextype_tree').hasClass('open')) {
        $form.closest('.carousel-inner').css('overflow', 'hidden');
      } else {
        $form.closest('.carousel-inner').css('overflow', 'visible');
      }
      $form.find('#div_indextype_tree').toggleClass('open');
      return $form.find('#tree_index_type_container').mCustomScrollbar('scrollTo', 'left');
    });


    $indexTypeTree.jstree({
      core: {
        check_callback: true,
        themes: {
          responsive: false
        },
        data: {
          url: configMap.path + '/gxcustomer/getIndexTypeTree'
        }
      },
      checkbox: {
        tie_selection: false,
        three_state: false
      },
      search: {
        show_only_matches: true
      },
      plugins: ['wholerow', 'checkbox', 'search']
    });
```