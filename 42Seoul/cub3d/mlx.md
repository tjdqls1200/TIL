mlx_init()

```c
void *mlx;

mlx = mlx_init();
```



- 그래픽 시스템에 connection을 만들고 void * 를 리턴한다. 이 void * 은 현재 MLX 인스턴스의 위치를 hold한다.

- If mlx_init() fails to set up the connection to the display, it will return  NULL.



mlx_new_window(mlx, 500, 500, "project_name");



mlx_loop(mlx);



```c
void *img;

int img_width;
int img_height;

img = mlx_xpm_file_to_image(mlx, "../textures/wall_n.xpm", &img_width, &img_height);

mlx_put_image_to_window(mlx, win, img, 50, 50);

```







```c
typedef struct	s_img
{
	void		*img_ptr;
	int			*data;
	
  int			size_l;
	int			bpp;
	int			endian;
}				t_img;


int main(void)
{
	t_img	img;

	img.data = (int *)mlx_get_data_addr(img.img_ptr, &img.bpp, &img.size_l, &img.endian);
}
```

