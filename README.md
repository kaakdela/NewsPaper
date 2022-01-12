# NewsPaper
Что вы должны сделать в консоли Django?
1.	Создать двух пользователей (с помощью метода User.objects.create_user).
2.	Создать два объекта модели Author, связанные с пользователями.
3.	Добавить 4 категории в модель Category.
4.	Добавить 2 статьи и 1 новость.
5.	Присвоить им категории (как минимум в одной статье/новости должно быть не меньше 2 категорий).
6.	Создать как минимум 4 комментария к разным объектам модели Post (в каждом объекте должен быть как минимум один комментарий).
7.	Применяя функции like() и dislike() к статьям/новостям и комментариям, скорректировать рейтинги этих объектов.
8.	Обновить рейтинги пользователей.
9.	Вывести username и рейтинг лучшего пользователя (применяя сортировку и возвращая поля первого объекта).
10.	Вывести дату добавления, username автора, рейтинг, заголовок и превью лучшей статьи, основываясь на лайках/дислайках к этой статье.
11.	Вывести все комментарии (дата, пользователь, рейтинг, текст) к этой статье.
1.  user1 = User.objects.create(username=’Mike’, first_name=’Mickey’)
    user2 = User.objects.create(username='Jake', first_name ='Jonson')
2. Author.objects.create(authorUser = user1)
Author.objects.create(authorUser=user2)
3 Category.objects.create(name=’IT’)
Category.objects.create(name=’Education’)
Category.objects.create(name=’IT, ’Education’’)
Category.objects.create(name=’IT’)

4. Post.objects.create(author=Author.objects.get(authorUser=User.objects.get(username=’Mike’)), categoryType=’NW’, title=’smth’, text=’smth txt’)
Post.objects.create(author=Author.objects.get(authorUser=User.objects.get(username=’Mike’)), categoryType=’AR’, title=’smth12’, text=’smth txt123’)
Post.objects.create(author=Author.objects.get(authorUser=User.objects.get(username=’Jake’)), categoryType=’AR’, title=’smt13h’, text=’smth2334’)
5.  p1=Post.objects.get(pk=1)
p2=Post.objects.get(pk=2)
p3=Post.objects.get(pk=3)
c1 = Category.objects.get(name=’IT’)
c2 = Category.objects.get(name=’Education’)
p1.postCategory.add(c1)
p2.postCategory.add(c1,c2)
p3.postCategory.add(c2)

6. 
Comment.objects.create(commentUser=User.objects.get(username=’Mike’), commentPost=Post.objects.get(pk=1), text=’comment1’)
Comment.objects.create(commentUser=User.objects.get(username=’Mike’), commentPost=Post.objects.get(pk=2), text=’comment2’)
Comment.objects.create(commentUser=User.objects.get(username=Jake), commentPost=Post.objects.get(pk=3), text=’comment3)
7.
Post.objects.get(pk=1).like()
Post.objects.get(pk=1).like()
Post.objects.get(pk=2).dislike()
Comment.objects.get(pk=1).dislike()
8.
Author.objects.get(authorUser=User.object.get(username=’Jake)).update_rating()
Author.objects.get(authorUser=User.object.get(username=’Mike’)).update_rating()
9. 
Author.objects.get(authorUser=User.object.get(username=’Mike’)).ratingAuthor
Best=Author.objects.all().order_by(‘-ratingAuthor)’.values(‘authorUser’,’ratingAuthor’)[0]
Print(best)
10 
