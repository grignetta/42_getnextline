CC      = cc
CFLAGS  = -Wall -Wextra -Werror
NAME    = libgnl.a
SRC     = get_next_line.c get_next_line_utils.c
OBJDIR  = obj
OBJ     = $(addprefix $(OBJDIR)/, $(SRC:.c=.o))

all: $(NAME)

$(OBJDIR)/%.o: %.c
	@mkdir -p $(OBJDIR)
	$(CC) $(CFLAGS) -I . -c $< -o $@

$(NAME): $(OBJ)
	ar rcs $(NAME) $(OBJ)

clean:
	rm -rf $(OBJDIR)

fclean: clean
	rm -f $(NAME)

re: fclean all

.PHONY: all clean fclean re